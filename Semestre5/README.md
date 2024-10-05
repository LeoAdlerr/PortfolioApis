# Projeto API com o Parceiro Acadêmico TecSUS (2024-1)

[Link para Repositório do Projeto](https://github.com/quarks-team/Projeto-Integrador-TecSUS)

## Objetivo

O principal objetivo deste projeto foi desenvolver um **Dashboard Web** de alta complexidade, capaz de processar e analisar faturas de energia e água de diversas unidades de clientes. O sistema permite que as empresas identifiquem oportunidades de redução de custos e otimização de contratos com concessionárias. Além disso, o dashboard oferece funcionalidades de geração de relatórios detalhados e alertas com base no consumo, possibilitando uma visão clara sobre o desempenho e os custos de cada unidade ou contrato.

## Minhas Contribuições

### Modelagem Dimensional
- Participei da modelagem dimensional, criando um banco de dados que facilitou a análise de grandes volumes de dados. Essa arquitetura permitiu gerar relatórios rápidos e eficientes, essenciais para lidar com múltiplas faturas por unidade, contrato e concessionária, sem comprometer a performance.
- Atuei em todas as fases da modelagem: concepção inicial, construção e implementação das tabelas de fato e dimensão. Trabalhei na definição de como as tabelas se relacionariam, levando em conta as especificidades dos dados de energia e água. Também desenvolvi as queries para carga de dados nas tabelas de fato, garantindo integridade e eficiência durante o processo de ETL.

<details>
<summary>Modelagem Dimensional</summary>
<img src="https://github.com/quarks-team/Projeto-Integrador-TecSUS-Database/blob/main/modelagem_banco_API_v.06.png">
</details>

### Backend com Node.js
Neste exemplo, desenvolvi um **controller** em Node.js que permitiu ao usuário carregar seus arquivos através do frontend e acompanhar o progresso do upload e do processo de ETL. Como o carregamento dos arquivos podia demorar até 5 minutos, era essencial manter o usuário informado sobre o tempo restante para a conclusão da carga.

<details>
<summary>Exemplo de Controller em Node.js</summary>
<pre><code>
@Controller('billing')
export class BillingController {
  constructor(private readonly service: BillingService) {}

  @Post('upload')
  @UseInterceptors(FilesInterceptor('files'))
  async uploadFiles(@UploadedFiles() files: Express.Multer.File[]) {
    const folderPath = path.join(__dirname, 'files');
    await mkdir(folderPath, { recursive: true });
    const filePromises = files.map(async (file) => {
      const filePath = path.join(folderPath, file.originalname);
      await writeFile(filePath, file.buffer);
      const log = (message: string) => {
        if (global.sseResponse) {
          global.sseResponse.write(
            `event: user-log\ndata: ${JSON.stringify({ message })}\n\n`,
          );
        }
      };
      await this.service.transform(file.originalname, filePath, log);
      if (global.sseResponse) {
        global.sseResponse.write(
          `event: user-log\ndata: ${JSON.stringify({
            message: \`O arquivo "\${file.originalname}" foi processado com sucesso.\`,
          })}\n\n`,
        );
      }
    });
    await Promise.all(filePromises);
    if (global.sseResponse) {
      global.sseResponse.write(
        `event: user-log\ndata: ${JSON.stringify({
          message: 'Todos os arquivos foram processados com sucesso.',
        })}\n\n`,
      );
      global.sseResponse.end();
    }
    return { message: 'Todos os arquivos foram processados com sucesso.' };
  }
}
</code></pre>
</details>

### ETL com Node.js
Implementei a lógica de **ETL** (Extração, Transformação e Carga) para inserir dados nas tabelas, verificando quais arquivos o usuário carregou e processando-os adequadamente. O sistema verificava se os dados carregados pertenciam a contratos ou contas de água ou energia, e só realizava a carga nas respectivas tabelas fato, garantindo a integridade e a coerência dos dados.

<details>
<summary>Exemplo de Transformação e Carga de Dados</summary>
<pre><code>
import { InjectRepository } from '@nestjs/typeorm';
import { Repository, In } from 'typeorm';
import { Time } from '../entity/time.entity';
import { WatterBill } from '../entity/watter-bill.entity';
import { WatterBillPayload } from '../request/watter-bill-payload';

export class IngestWatterBill {
  constructor(
    @InjectRepository(Time) private readonly timeRepo: Repository<Time>,
    @InjectRepository(WatterBill)
    private readonly billRepo: Repository<WatterBill>,
  ) {}

  async execute(watterBills: WatterBillPayload[]) {
    const times: Partial<Time>[] = [];
    const bills: Partial<WatterBill>[] = [];
    watterBills.forEach((bill) => {
      const [day, month, year] = bill['Conta do Mês'].split('/').map(Number);
      const billDate = new Date(year, month - 1, day);
      bills.push({
        rgiCode: bill['Código de Ligação (RGI)'],
        billDate: billDate,
        hidrometer: bill.Hidrômetro,
        watterConsume: Number.parseFloat(
          bill['Consumo de Água m³'].replace(',', ''),
        ),
        wastePipeConsume: Number.parseFloat(
          bill['Consumo de Esgoto m³'].replace(',', ''),
        ),
        watterValue: Number.parseFloat(bill['Valor Água R$'].replace(',', '')),
        wastePipeValue: Number.parseFloat(
          bill['Valor Esgoto R$'].replace(',', ''),
        ),
        total: Number.parseFloat(bill['Total R$'].replace(',', '')),
        plant: bill.Planta,
        provider: 'null',
      });
      times.push({
        month: month.toString(),
        year: year.toString(),
      });
    });
    // Processa dados, verifica duplicidade e insere dados nas tabelas de tempo e conta
    // Carga nas tabelas de fato ocorre somente após verificações necessárias
    try {
      const distinctTimes = this.getDistinctObjects(times);
      const existingTimes = await this.timeRepo.find({
        where: {
          month: In(distinctTimes.map((time) => time.month)),
          year: In(distinctTimes.map((time) => time.year)),
        },
      });
      const newTimes = distinctTimes.filter(
        (time) => !existingTimes.find((existing) => existing.month === time.month && existing.year === time.year),
      );
      await this.timeRepo.save(newTimes);
    } catch (error) {
      console.error('Error saving times:', error);
    }
  }

  // Função auxiliar para remover duplicidade de objetos
  getDistinctObjects(array) {
    return array.filter(
      (obj, index, self) =>
        index ===
        self.findIndex((t) => t.month === obj.month && t.year === obj.year),
    );
  }
}
</code></pre>
</details>

### Verificação e Carga nas Tabelas Fato
Após as transformações, o processo de carga nas tabelas fato de água ou energia era executado. A carga só ocorria se houvesse novos dados relevantes, garantindo eficiência e evitando duplicidades.

<details>
<summary>Carga nas Tabelas Fato</summary>
<pre><code>
async execute() {
  const hasSomeContract = await this.contractRepo.count();
  const hasSomeBill = await this.billRepo.count();
  if (hasSomeBill > 0 && hasSomeContract > 0) {
    await this.factRepo.clear();
    await this.factRepo.query(
      `INSERT INTO fato_conta_agua (
        contrato_agua_id,
        conta_agua_id,
        unidade_cliente_id,
        tempo_id,
        local_planta_id,
        total_conta_agua,
        total_consumo_agua,
        total_consumo_esgoto,
        total_valor_agua,
        total_valor_esgoto
      )
      SELECT 
        c.contrato_agua_id, 
        conta.conta_agua_id, 
        u.unidade_cliente_id, 
        t.tempo_id, 
        l.local_planta_id,
        SUM(conta.total_conta_agua) AS total_conta_agua, 
        SUM(conta.consumo_agua) AS total_consumo_agua,
        SUM(conta.consumo_esgoto) AS total_consumo_esgoto, 
        SUM(conta.valor_agua) AS total_valor_agua, 
        SUM(conta.valor_esgoto) AS total_valor_esgoto
      FROM conta_agua conta
      INNER JOIN contrato_agua c ON conta.codigo_rgi = c.codigo_rgi
      INNER JOIN unidade_cliente u ON c.cnpj = u.cnpj
      INNER JOIN local_planta l ON l.planta = conta.planta_agua
      INNER JOIN tempo t ON t.tempo_mes = DATE_FORMAT(conta.agua_conta_mes, '%m') 
                          AND t.tempo_ano = DATE_FORMAT(conta.agua_conta_mes, '%Y')
      GROUP BY c.contrato_agua_id, conta.conta_agua_id, u.unidade_cliente_id, t.tempo_id, l.local_planta_id;`
    );
  }
}
</code></pre>
</details>

### Aprendizado Efetivo

Durante o desenvolvimento deste projeto, aprendi muito sobre várias áreas fundamentais da construção de sistemas complexos, como:

#### Modelagem Dimensional
- Trabalhei intensamente com modelagem dimensional, essencial para lidar com grandes volumes de dados e para garantir relatórios ágeis.

#### Node.js
- O uso de Node.js em backends escaláveis foi vantajoso tanto pela performance quanto pela facilidade de integração com bibliotecas de processamento de dados.

#### SQL e Consultas Otimizadas
- A otimização de queries para grandes bases de dados, principalmente aquelas relacionadas ao cálculo de métricas e agregações, foi crucial para manter a eficiência do sistema.

#### DevOps
- Aprendi sobre os princípios e práticas do DevOps, que enfatizam a colaboração entre as equipes de desenvolvimento e operações para automatizar e melhorar o ciclo de vida do desenvolvimento de software. A implementação de uma esteira DevOps permitiu integrar testes automatizados, integração contínua e entrega contínua (CI/CD), garantindo que as atualizações e implementações fossem mais rápidas, seguras e confiáveis. Isso não apenas melhorou a qualidade do código, mas também aumentou a eficiência do processo de desenvolvimento como um todo.


### Conclusão

Este projeto foi uma grande oportunidade para expandir minhas habilidades como desenvolvedor, especialmente ao trabalhar com tecnologias novas para mim, como Node.js e modelagem dimensional. O uso de Node.js no backend permitiu criar APIs eficientes e escaláveis, o que me proporcionou um aprendizado valioso em uma stack que eu ainda não dominava. Além disso, a modelagem dimensional aprimorou minha capacidade de organizar e estruturar dados para análises mais poderosas, otimizando o desempenho de visualizações no Power BI.

A implementação de uma esteira de DevOps garantiu um ciclo de desenvolvimento contínuo e rastreável, permitindo um processo ágil e confiável. No final, o sistema desenvolvido oferece insights importantes para o cliente, melhorando a gestão de contratos e a tomada de decisões estratégicas. O projeto me transformou em um desenvolvedor mais completo, integrando habilidades de backend, ETL e visualização de dados em um único ecossistema eficiente e bem estruturado.
