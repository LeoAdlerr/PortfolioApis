<h3>Em 2024-1 foi trabalhado um projeto API com o parceiro acadêmico Tecsus</h3> 

<h4><a  href= "https://github.com/quarks-team/Projeto-Integrador-TecSUS" > Link para Repositorio do projeto </a></h4>

### Objetivo
O principal objetivo deste projeto foi desenvolver um **Dashboard Web** de alta complexidade, capaz de processar e analisar faturas de energia, água de diversas unidades de clientes. O sistema permite que as empresas identifiquem oportunidades de redução de custos e otimização de contratos com concessionárias. O dashboard oferece funcionalidades de geração de relatórios detalhados e alertas baseados no consumo, possibilitando uma visão clara e direta sobre o desempenho e os custos de cada unidade ou contrato.

### Minhas Contribuições

<summary> Modelagem dimensional
	<details>
	<img src="https://github.com/quarks-team/Projeto-Integrador-TecSUS-Database/blob/main/modelagem_banco_API_v.06.png">	
	</details>
</summary>
<summary> Backend Node.js
	<details>
		<pre>
			<code>
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
            event: user-log\ndata: ${JSON.stringify({ message })}\n\n,
          );
        }
      };
      await this.service.transform(file.originalname, filePath, log);
      // Emit an event of process progress friendly for SSE
      if (global.sseResponse) {
        global.sseResponse.write(
          event: user-log\ndata: ${JSON.stringify({
            message: O arquivo "${file.originalname}" foi processado com sucesso.,
          })}\n\n,
        );
      }
    });
    await Promise.all(filePromises);
    // Emit a conclusion event for SSE
    if (global.sseResponse) {
      global.sseResponse.write(
        event: user-log\ndata: ${JSON.stringify({
          message: 'Todos os arquivos foram processados com sucesso.',
        })}\n\n,
      );
      global.sseResponse.end();
    }
    return { message: 'Todos os arquivos foram processados com sucesso.' };
  }
			</code>
		</pre>
	</details>
</summary>
<summary> ETL Node.js
	<details>
    <summary> Fazendo todas as transdormacoes necessarias e inserindo em todas as tabelas
      <details>
        <pre>
          <code>
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
    try {
      const distinctTimes = this.getDistinctObjects(times);
      const existingTimes = await this.timeRepo.find({
        where: {
          month: In(distinctTimes.map((time) => time.month)),
          year: In(distinctTimes.map((time) => time.year)),
        },
      });
      const existingTimeMap = new Set(
        existingTimes.map((time) => ${time.month}-${time.year}),
      );
      const newTimes = distinctTimes.filter(
        (time) => !existingTimeMap.has(${time.month}-${time.year}),
      );
      await this.timeRepo.save(newTimes);
    } catch (error) {
      console.error('Error saving times:', error);
    }
    try {
      const distinctBills = this.getDistinctBills(bills);
      const existingBills = await this.billRepo.find({
        where: distinctBills.map((bill) => ({
          rgiCode: bill.rgiCode,
          billDate: bill.billDate,
          hidrometer: bill.hidrometer,
          plant: bill.plant,
        })),
      });
      const existingBillMap = new Set(
        existingBills.map(
          (bill) =>
            ${bill.rgiCode}-${bill.billDate.getTime()}-${bill.hidrometer}-${bill.plant},
        ),
      );
      const newBills = distinctBills.filter(
        (bill) =>
          !existingBillMap.has(
            ${bill.rgiCode}-${bill.billDate.getTime()}-${bill.hidrometer}-${bill.plant},
          ),
      );
      await this.billRepo.save(newBills);
    } catch (error) {
      console.error('Error saving bills:', error);
    }
  }
  getDistinctObjects(array) {
    return array.filter(
      (obj, index, self) =>
        index ===
        self.findIndex((t) => t.month === obj.month && t.year === obj.year),
    );
  }
  
  getDistinctBills(array) {
    return array.filter(
      (obj, index, self) =>
        index ===
        self.findIndex(
          (t) =>
            t.rgiCode === obj.rgiCode &&
            t.billDate.getTime() === obj.billDate.getTime() &&
            t.hidrometer === obj.hidrometer &&
            t.plant === obj.plant,
        ),
    );
  }
  }
          </code>
        </pre>
      </details>
      <summary> Chamando cada uma das transformacoes e cargas e garantindo que apenas os arquivos carregados pelo usuario tenham o processo de carga realizado. Perceba que a carga na tabela fato de agua ou energia depende
      do tipo de arquivo que o usuario enviou, isso acontece pois so vao existir dados novos nas tabelas dimensionais relacionais de energia se houve uma carga de um arquivo de contas ou contratos de energia, o mesmo
      ocorre para a tabela fato de agua, claro que se arquivos de ambos os tipos forem carregados as duas tabelas fato terao suas cargas realizadas 
        <details>
          <pre>
            <code>
            async transform(
    fileName: string,
    path: string,
    log: (message: string, technical?: boolean) => void,
  ): Promise<string> {
    let bills = [];
    log(${fileName}: Iniciando o processo de transformação ETL...);
    log(${fileName}: Carregando dados do arquivo.);
    try {
      const obj = await csvToJson().fromFile(path);
      bills = obj;
      log(${fileName}: Dados carregados com sucesso.);
    } catch (error: any) {
      log(${fileName}: Erro ao carregar dados:  + error.message, true);
      throw new Error(${fileName}: Falha ao carregar dados do arquivo.);
    }
    const name = fileName.substring(0, fileName.length - 4);
    log(${fileName}: Identificando o tipo de arquivo:  + name);
    try {
      switch (name) {
        case 'con_agua':
          log(${fileName}: Processando contratos de água...);
          const watterContracts: WatterContractPayload[] = bills;
          await this.ingestWatterContract.execute(watterContracts);
          log(
            ${fileName}: Contratos de água processados com sucesso. Tabelas dimensão atualizadas.,
          );
          log(${fileName}: Gerando tabela fato de água...);
          await this.generateWatterFact.execute();
          log(${fileName}: Tabela fato de água gerada com sucesso.);
          break;
        case 'con_energia':
          log(${fileName}: Processando contratos de energia...);
          const energyContracts: EnergyContractPayload[] = bills;
          await this.ingestEnergyContract.execute(energyContracts);
          log(
            ${fileName}: Contratos de energia processados com sucesso. Tabelas dimensão atualizadas.,
          );
          log(${fileName}: Gerando tabela de fato de energia...);
          await this.generateEnergyFact.execute();
          log(${fileName}: Tabela fato de energia gerada com sucesso.);
          break;
        case 'pro_energia':
          log(${fileName}: Processando contas de energia...);
          const energyBills: EnergyBillPayload[] = bills;
          await this.ingestEnergyBill.execute(energyBills);
          log(
            ${fileName}: Contas de energia processadas com sucesso. Tabelas dimensão atualizadas.,
          );
          log(${fileName}: Gerando tabela fato de energia...);
          await this.generateEnergyFact.execute();
          log(${fileName}: Tabela fato de energia gerado com sucesso.);
          break;
        case 'pro_agua':
          log(${fileName}: Processando contas de água...);
          const watterBills: WatterBillPayload[] = bills;
          await this.ingestWatterBill.execute(watterBills);
          log(
            ${fileName}: Contas de água processadas com sucesso. Tabelas dimensão atualizadas.,
          );
          log(${fileName}: Gerando tabela fato de água...);
          await this.generateWatterFact.execute();
          log(${fileName}: Tabela fato de água gerados com sucesso.);
          break;
        default:
          log(${fileName}: Tipo de arquivo inválido.);
          throw new Error(${fileName}: Nome ou tipo de arquivo inválido.);
      }
      log(${fileName}: Processo de ETL no arquivo concluído com sucesso.);
      return 'billing-ingestion: hmm good ingestion';
    } catch (error) {
      log(${fileName}: Erro no processo de ETL:  + error.message);
      throw error;
    }
  }
            </code>
          </pre>
          </details>
        </summary>
    </summary>
    <summary> Carga nas tabelas fato, apos as verificacoes necessarias a carga ocorre
      <details>
        <pre>
          <code>
          async execute() {
    const hasSomeContract = await this.contractRepo.count();
    const hasSomeBill = await this.billRepo.count();
    console.log(hasSomeBill, hasSomeContract);
    if (hasSomeBill > 0 && hasSomeContract > 0) {
      await this.factRepo.clear();
      await this.factRepo.query(INSERT INTO fato_conta_agua (
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
    FROM 
        conta_agua conta
    INNER JOIN 
        contrato_agua c ON conta.codigo_rgi = c.codigo_rgi
    INNER JOIN 
        unidade_cliente u ON c.cnpj = u.cnpj
    INNER JOIN 
        local_planta l ON l.planta = conta.planta_agua
    INNER JOIN 
        tempo t ON t.tempo_mes = DATE_FORMAT(conta.agua_conta_mes, '%m') 
                  AND t.tempo_ano = DATE_FORMAT(conta.agua_conta_mes, '%Y')
    GROUP BY 
        c.contrato_agua_id, 
        conta.conta_agua_id, 
        u.unidade_cliente_id, 
        t.tempo_id, 
        l.local_planta_id;);
    }
  }
}
          </code>
        </pre>
      </details>
    </summary>
	</details>
</summary>

(Contribuições futuras serão detalhadas nesta seção, relacionadas ao backend, frontend e integração de dados.)

### Aprendizado Efetivo

Durante o desenvolvimento deste projeto, obtive um aprendizado significativo em várias áreas fundamentais para a construção do sistema. Abaixo estão os principais tópicos de aprendizado:

#### Modelagem Dimensional
- O banco de dados foi criado dentro da concepcao de modelo dimensional, o que facilitou a análise de grandes volumes de dados, permitindo criar relatórios rápidos e eficientes. Isso foi crucial para que o sistema pudesse lidar com múltiplas faturas por unidade, contrato e concessionária, sem perder a performance.
- Participei ativamente em todas as fases da modelagem dimensional, desde a concepção inicial até a construção e implementação das tabelas de fato e dimensão. Colaborei na definição de como cada tabela se relacionaria dentro do modelo, considerando as particularidades dos dados de energia e água. Além disso, desenvolvi as queries de carga de dados para as tabelas de fato, garantindo a integridade dos dados e o desempenho eficiente durante o processo de ETL.

#### ETL (Extração, Transformação e Carga)
- Implementei processos de **ETL (Extração, Transformação e Carga)** para integrar dados de várias fontes (como arquivos CSV, APIs de concessionárias e bases de dados legadas). O uso de ferramentas como o **Apache Airflow** ajudou a automatizar essas etapas, garantindo a precisão e a consistência dos dados no banco centralizado.

#### Node.js
- Na parte do backend, utilizei **Node.js** para desenvolver a API responsável pela coleta e fornecimento dos dados das faturas. Isso permitiu a construção de uma aplicação altamente performática e escalável, capaz de atender múltiplos clientes simultaneamente.

#### Power BI
- No frontend, implementei dashboards e relatórios interativos utilizando **Power BI** para fornecer insights visuais em tempo real sobre o consumo de recursos (água, energia e gás). O Power BI foi essencial para o desenvolvimento de gráficos dinâmicos, permitindo que os usuários acompanhassem tendências e identificassem anomalias no consumo.

#### Embedding Power BI na Aplicação
- Um dos desafios técnicos mais interessantes foi a integração dos **dashboards do Power BI** diretamente no sistema web. Para isso, utilizei a técnica de embedding, que permitiu a exibição dos relatórios e gráficos de forma interativa, dentro da própria aplicação. A integração com o backend permitiu controlar o acesso e personalizar as visualizações conforme as permissões do usuário.

### Conclusão

Este projeto foi uma excelente oportunidade para consolidar meus conhecimentos em **ETL**, **modelagem dimensional**, **desenvolvimento backend com Node.js** e **visualização de dados com Power BI**. Além disso, a implementação da **esteira de DevOps** garantiu que o ciclo de desenvolvimento fosse eficiente e rastreável. O dashboard web criado fornece insights valiosos que ajudarão os clientes da TecSUS a gerenciar seus contratos de maneira mais eficiente, reduzindo custos e melhorando a tomada de decisões estratégicas.
