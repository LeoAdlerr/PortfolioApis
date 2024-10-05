# Portfólio dos Projetos API's (Aprendizagem por Projetos Integradores) - FATEC Jessen Vidal

##  Leonardo Adler da Silva

Olá, sou **Leonardo Adler da Silva**, um apaixonado estudante de Banco de Dados na Fatec Jessen Vidal. Ao longo da minha jornada acadêmica, tive a oportunidade de trabalhar com metodologias ágeis e diversas tecnologias, resultando em projetos empolgantes que compartilho abaixo. 

### 🚀 Projetos por Semestre

- **1º Semestre (Fatec/Interno)**: [🔗 Link para o portfólio 1º Semestre Python](https://github.com/LeoAdlerr/PortfolioApis/tree/main/1Semestre)

- **2º Semestre (DomRock)**: [🔗 Link para o portfólio 2º Semestre Java](https://github.com/LeoAdlerr/PortfolioApis/tree/main/2Semestre)

- **3º Semestre (IACIT)**: [🔗 Link para o portfólio 3º Semestre Java - SpringBoot](https://github.com/LeoAdlerr/PortfolioApis/tree/main/3Semestre)

- **4º Semestre (JAIA)**: [🔗 Link para o portfólio 4º Semestre SpringBoot - Vue.JS](https://github.com/LeoAdlerr/PortfolioApis/tree/main/4Semestre)

---

##  Feito com entusiasmo por Leonardo Adler da Silva


<h3>Em 2021-2 foi trabalhado um projeto API com cliente interno (professores da Fatec)</h3>

## Objetivo do Projeto
O objetivo deste projeto foi desenvolver um programa interativo que fornecesse estatísticas sobre a Covid-19 no estado de São Paulo. Através da coleta e visualização de dados, o programa busca informar a população sobre a evolução da pandemia, permitindo uma melhor compreensão dos impactos e das medidas tomadas ao longo do tempo.

## Tecnologias Utilizadas
- Python
- Pandas
- Matplotlib

## Minhas Contribuições
Durante o desenvolvimento do projeto, participei ativamente das seguintes atividades:
- **Coleta e manipulação de dados:** Utilizei a biblioteca Pandas para extrair dados relevantes do arquivo CSV, filtrando informações específicas sobre o estado de São Paulo.
  <details>
    <summary>Exemplo de código de Coleta e Manipulação de Dados</summary>
    <pre>
    <code>
    import pandas as pd

    # Carregar os dados
    df = pd.read_csv('caso_full.csv')

    # Filtrar dados para o estado de SP
    df_sp = df[df['estado'] == 'SP']
    </code>
    </pre>
  </details>
- **Criação de gráficos:** Implementei visualizações utilizando Matplotlib para apresentar as estatísticas de forma clara e intuitiva, facilitando a compreensão dos dados pelo usuário.
  <details>
    <summary>Exemplo de código de Criação de Gráficos</summary>
    <pre>
    <code>
    import matplotlib.pyplot as plt

    # Gráfico de casos confirmados
    plt.plot(df_sp['data'], df_sp['casos_confirmados'])
    plt.title('Casos Confirmados de Covid-19 em SP')
    plt.xlabel('Data')
    plt.ylabel('Casos Confirmados')
    plt.show()
    </code>
    </pre>
  </details>
- **Interatividade do programa:** Estruturei um sistema de menus que permite ao usuário selecionar diferentes opções de análise, tornando a experiência interativa e dinâmica.
  <details>
    <summary>Exemplo de código de Interatividade</summary>
    <pre>
    <code>
    def menu():
        print("1. Ver dados")
        print("2. Gerar gráfico")
        choice = input("Escolha uma opção: ")
        return choice

    # Exemplo de chamada do menu
    option = menu()
    </code>
    </pre>
  </details>

## Aprendizados Efetivos
Este projeto me proporcionou uma valiosa experiência em programação e análise de dados. Aprendi:
- **Uso de bibliotecas em Python:** A importância das bibliotecas Pandas e Matplotlib na manipulação e visualização de dados.
- **Estruturas de controle:** A utilização de laços e condicionais para criar uma interface interativa.
- **Análise de dados:** Como transformar dados brutos em informações úteis e significativas para o público.

## Considerações Finais
Este projeto marcou meu primeiro contato com programação e análise de dados, e mesmo sendo um iniciante, foi gratificante ver a criação de uma ferramenta que não apenas reúne informações, mas também fornece insights reais e relevantes aos usuários. A experiência adquirida foi essencial para meu desenvolvimento pessoal e profissional, e me motivou a continuar aprendendo e aprimorando minhas habilidades na área de tecnologia e ciência de dados.

<br><br>

<h3> Em 2022-1 foi trabalhado um projeto API com o parceiro acadêmico DomRock </h3> 
 
# Projeto de Gestão de Ativação de Clientes - Dom Rock

## Visão e Objetivo do Projeto
O desafio consiste na gestão de ativação de clientes na plataforma Dom Rock. Precisamos de uma solução que seja orientada a entrada de dados de parâmetros e variáveis de cada cliente para alocar recursos na plataforma Dom Rock, entrada de dados e estimativa de consumo de recursos (baseado em volume de dados de cliente, quantidade de usuários e outros) e gere relatórios e consultas, mas, principalmente, tenha a base de dados modelada adequadamente para futuras integrações com outros sistemas. Para realizar o desafio, foi necessária a criação de interfaces para cada etapa do programa visando facilitar a ativação delas e dos cadastros posteriormente, além de tornar o processo visível aos clientes.

## Tecnologias Utilizadas no Projeto
<ul>
  <li><strong>Java:</strong> 
    <br>A linguagem de programação utilizada com as lógicas para inserção, selecionar, deletar e excluir. Assim conectando o banco de dados à aplicação Desktop.
  </li>
  <li><strong>SqlServer:</strong> 
    <br>Foi utilizado um banco na nuvem Azure (SqlServer) onde os dados de login e dos pedidos dos clientes foram armazenados.
  </li>
  <li><strong>JavaSwing:</strong> 
    <br>Todo o visual e design da aplicação foi feito usando essa tecnologia, desde a tela de login até a tela gold.
  </li>
  <li><strong>Maven:</strong> 
    <br>Utilizado para versionar e enviar o código no Git, assim facilitando a todos os desenvolvedores e usuários a utilizarem o código mais atualizado no momento, principalmente na manutenção de bibliotecas Java utilizadas, algo que durante o processo e na instalação do código final facilita o uso do mesmo.
  </li>
</ul>

## Contribuições Individuais

<details>
<summary>Classes DAO de Conexão com BD</summary>
  <p><br>
    - Foi criada uma classe DAO chamada ConnectionManager, que contém o objeto com a conexão para o Banco de Dados e que, por consequência, todas as demais classes DAO irão utilizar, assim não sendo necessário abrir uma nova conexão a cada evento da aplicação:
    <br><br>
    * [classe ConnectionManager exemplo]
    <pre><code>
    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(
            "jdbc:sqlserver://XXXXXX.DDDDDD.WWWWWW.net;databaseName=DDDD;user=SSSSSS;password=***********"
        );
    }
    </code></pre>
  </p>
</details>

<details>
<summary>Classes DAO dos Objetos</summary>
  <p><br>
    - Foi criada uma classe DAO chamada DaoCliente, onde todo evento que envolve o banco de dados na tabela/entidade Cliente é realizado:
    <br><br>
    * [classe DaoCliente exemplo]
    <pre><code>
    public void criarCl(Cliente c1) {
        this.c1 = c1;
        Connection con = null;
        try {
            con = ConnectionManager.getConnection();
            String insert_sql = "insert into cliente (cnpj, entrega_minimas, entregas_possiveis, 
            nome_cliente, objetivo, setor, razao_social, id_solucao) values (?, ?, ?, ?, ?, ?, ?, ?)";
            PreparedStatement pst;
            pst = con.prepareStatement(insert_sql);
            pst.setObject(1, c1.getvCNPJ_Cliente());
            pst.setObject(2, c1.getvEntregaM_Cliente());
            pst.setObject(3, c1.getvEntregaP_Cliente());
            pst.setObject(4, c1.getvNome_Cliente());
            pst.setObject(5, c1.getvObjetivo_Cliente());
            pst.setObject(6, c1.getvSetor_Cliente());
            pst.setObject(7, c1.getvSocial_Cliente());
            pst.setObject(8, c1.getvId_Solucao());
            pst.executeUpdate();
        } catch (SQLException e) {
            e.printStackTrace();
            throw new RuntimeException("Erro ao inserir os dados!", e);
        } finally {
            try {
                if (con != null)
                    con.close();
            } catch (SQLException e) {
                e.printStackTrace();
                throw new RuntimeException("Erro ao fechar conexão", e);
            }
        }
    }
    </code></pre>
    Neste exemplo, o método criarCl() recebe um objeto da entidade Cliente que, por sua vez, utiliza os getters presentes nos atributos do objeto da Classe Cliente para criar um novo registro na tabela cliente com os valores especificados na view. 
  </p>
</details>

<details>
<summary>Modelagem Relacional</summary>
  <p><br>
    Foi gerada uma modelagem relacional para satisfazer a necessidade de cadastrar clientes e seus pedidos/produtos.
    <br><br>
    *[Modelagem da aplicação]
    <br><br>
	  <img src="https://github.com/LeoAdlerr/PortfolioApis/assets/88751032/5c21e53a-fb14-468f-8472-d8ed36985de5">  
</details>

<details>
<summary>Orientação a Objeto e Classes que Representam Algo na Vida Real</summary>
  <p><br>
    No exemplo em questão, represento a tabela cliente, que contém os valores que serão cadastrados pela aplicação no banco de dados, ou seja, os valores que representam esse cliente na vida real:
    <br><br>
    //Classe
    <pre><code>
    public class Cliente {
        //Atributos
        private String vNome_Cliente;
        private String vCNPJ_Cliente;
        private String vNome_Cliente2;
        private String vCNPJ_Cliente2;
        private String vSocial_Cliente;
        private String vSetor_Cliente;
        private String vSolucao_Cliente;
        private String vObjetivo_Cliente;
        private String vEntregaM_Cliente;
        private String vEntregaP_Cliente;
        private int vId_Cliente;
        private int vId_Solucao;
        private int vId_Produto;
        private int vId_Escolha;
    }
    </code></pre>
  </p>
</details>

## Aprendizado Efetivo:
### Orientação a Objeto:
- O principal aprendizado foi a criação de classes que representam as tabelas do banco de dados com os mesmos atributos; essa tarefa de mapear e representar os registros na aplicação se tornou muito mais prática.

### MVC (Model, View, Controller):
- Com classes para representar a modelagem do BD, separadas das classes de visão e conexão com o Banco, cada tarefa se tornou mais específica, além da aplicação ser mais fácil de ser compreendida por qualquer desenvolvedor, já que cada parte do código segue seu padrão.

### Modelagem Relacional:
- Para representar algo na vida real, foi necessário criar uma modelagem relacional. Nesse projeto, isso foi imprescindível, pois os dados de uma visão dependiam dos valores inseridos na anterior, inclusive com a possibilidade de uma visão que poderia ter registros múltiplos da anterior para o mesmo cliente (relacionamento 1,N ou um para muitos) e outras que apenas um registro era possível (relacionamento 1,1 ou um para um).

Os principais aprendizados incluem:
- **Importância da Comunicação:** A comunicação eficaz entre os membros da equipe e stakeholders foi fundamental para o progresso do projeto e a resolução de problemas.

- **Adaptação a Mudanças:** A capacidade de adaptar o escopo e as prioridades do projeto em resposta a feedbacks contínuos melhorou significativamente a qualidade do produto final.

- **Desenvolvimento Ágil:** A aplicação de metodologias ágeis permitiu uma entrega contínua de funcionalidades, garantindo que o projeto permanecesse alinhado com as expectativas do cliente.

## 💡Considerações Finais
O projeto foi uma experiência rica em aprendizado e colaboração. Durante o desenvolvimento, enfrentamos desafios como a definição dos requisitos do sistema e a integração entre diferentes tecnologias, que foram superados com o esforço conjunto da equipe.

<br><br>


<h3> Em 2023-1 foi trabalhado um projeto API com o parceiro acadêmico IACIT </h3> 

* [Link para o Repositório](https://github.com/DatatechOffice/Api_Iacit)

<h4> Visão e objetivo do projeto </h4>
Desenvolver um sistema web, onde fosse possível realizar a extração e tratamento de dados meteorológicos através do site INEP fornecido pelo parceiro, além da persistência dos mesmos e, por fim, a visualização dos dados de forma que decisões pudessem ser realizadas. Para tal, foram utilizados gráficos e a filtragem dos dados pelo usuário.

<h4>Tecnologias utilizadas no Projeto</h4>

- HTML, CSS e Bootstrap: 
  Todo o visual e design da página web foram feitos utilizando essas tecnologias, isso inclui os gráficos com os dados meteorológicos, auxiliando-se das lógicas do JavaScript para tal.
  
- JavaScript:
  Lógica das páginas, seja restrições das mesmas, preenchimentos ou a filtragem dos dados selecionados pelos usuários, conectando e utilizando as APIs criadas em Java/Spring Boot.
  
- Java e Spring Boot:
  Foram feitas rotinas para persistir a base de dados meteorológicos e a criação das APIs REST conectando o banco de dados que contém os dados meteorológicos com as páginas, permitindo que os resultados sejam enviados em formato JSON para serem tratados pelo JavaScript.
  
- Python: 
  Uma rotina para captação dos dados em CSV fornecidos pelo cliente foi criada, permitindo a criação de um CSV com os valores de todos os períodos agregados, possibilitando sua persistência usando Java.
  
- PostgreSQL: 
  Foi o banco de dados de preferência da empresa contratante e utilizado para armazenar os dados meteorológicos de forma que fosse possível utilizá-los num programa, além de apresentá-los em um formato e tipo que facilitassem o uso.
  
- Maven: 
  Utilizado para versionar e enviar o código no Git, facilitando a todos os desenvolvedores e usuários a utilização do código mais atualizado, principalmente na manutenção de bibliotecas Java utilizadas.

<h4>Contribuições Individuais</h4>

<details>
<summary>API Rest</summary>
- Usando Spring Boot, criei as APIs a serem consumidas, conectando-as ao banco SQL para buscar os dados filtrados pelo frontend. A lógica foi pensada para contemplar quaisquer pesquisas feitas, além do CRUD com as telas de login.

<pre><code>
@RestController
@RequestMapping("/api/v1/dados")
public class DadosController {

    @Autowired
    private DadosService dadosService;

    @GetMapping
    public List<Dados> getDados(@RequestParam(required = false) String filtro) {
        return dadosService.buscarDadosFiltrados(filtro);
    }

    @PostMapping
    public Dados criarDados(@RequestBody Dados dados) {
        return dadosService.salvarDados(dados);
    }
}
</code></pre>
</details>

<details>
<summary>Manipulação de dados - Na persistência</summary>
- Desenvolvi scripts em Java para popular o banco com os dados vindos do CSV, garantindo que apenas uma instância de cada Estado fosse inserida nas tabelas.

<pre><code>
public void popularBancoComCSV(String caminhoCSV) {
    List<Estado> estados = lerCSV(caminhoCSV);
    for (Estado estado : estados) {
        if (!estadoRepository.existsById(estado.getId())) {
            estadoRepository.save(estado);
        }
    }
}
</code></pre>
</details>

<details>
<summary>Orientação a Objeto e classes que representam algo da vida real</summary>
- As classes foram estruturadas para representar a Radiação Global das cidades, com atributos que refletem o horário da coleta e o valor da radiação.

<pre><code>
@Entity
public class RadiacaoGlobal {
    @Id
    private Long id;
    private String cidade;
    private LocalDateTime horarioColeta;
    private Double valorRadiacao;

    // Getters e Setters
}
</code></pre>
</details>

<details>
<summary>Polimorfismo</summary>
- Utilizando interfaces do Hibernate, foi possível mapear as colunas e tabelas do banco de dados com as classes que representam cada respectiva entidade.

<pre><code>
public interface RadiacaoRepository extends JpaRepository<RadiacaoGlobal, Long> {
    List<RadiacaoGlobal> findByCidade(String cidade);
}
</code></pre>
</details>


<h4>Aprendizado Efetivo:</h4>

<summary>API's Rest:</summary>
- Foi o principal aprendizado, permitindo a criação de diversos tipos de aplicativos web que necessitam de mecanismos de busca ou apresentação de dados, como gráficos. O mais importante foi entender como construir uma API REST em Spring Boot.

<summary>Protocolo HTTP e APIs REST:</summary>
- Aprendi sobre o protocolo HTTP e como ele serve como a base para a comunicação entre o cliente e o servidor. As APIs REST utilizam os métodos HTTP (como GET, POST, PUT e DELETE) para realizar operações em recursos, permitindo a troca de dados em formato JSON. Essa interligação é fundamental para a construção de aplicativos web que se comunicam de forma eficiente com o backend.

<summary>Orientação a Objeto:</summary>
- As classes da pasta Entity, com o auxílio do Hibernate, representam as tabelas do banco de dados e suas correspondências com entidades da vida real.

<summary>Polimorfismo:</summary>
- A separação das classes em Interfaces, Services, Entities (Repositories) e Controllers facilitou a herança de funcionalidades e o controle das partes do processo, economizando linhas de código.

<summary>Persistência:</summary>
- Utilizando orientação a objeto/polimorfismo, implementamos todo o processo desde o download dos CSVs com dados meteorológicos, tratamento desses arquivos e inserção no banco, considerando a quantidade massiva de informações.



<h4>Conclusão</h4>
O projeto desenvolvido em parceria com a IACIT foi uma experiência enriquecedora, proporcionando uma compreensão profunda sobre o uso de APIs, a manipulação de dados e a implementação de soluções web eficientes. O aprendizado do framework Spring foi crucial para estruturar as aplicações, permitindo o desenvolvimento de sistemas robustos e escaláveis, alinhando teoria e prática de forma significativa.

<br><br>
  
 <h3> Em 2023-2 foi trabalhado um projeto API com o parceiro acadêmico JAIA </h3> 
 
* [Link para o Repositório do projeto](https://github.com/Great-Pretender/GreatPretender-API)

<h4> Visão e objetivo do projeto </h4>

Um Sistema desenvolvido para controlar o estado de um imóvel em, com os resultados
 exportados num Laudo de Inspeção Predial, além de gerenciar manutenções preventivas
 e corretivas de não conformidades que possam estar colocando em risco um patrimônio,
 garantindo assim a segurança, qualidade e manutençao ou gerenciamento de riscos.

<h4>Tecnologias utilizadas no Projeto</h4>

<h5>Backend: </h5>

- Java e SpringBoot:
  <br><br>
  	-As API's Rest para o CRUD da aplicação foram feitas em SpringBoot;
  
	-Segurança de Logins e geração de relatórios através do Spring Security;
  <br><br>
- Oracle Cloud(AWS): 
  <br><br>
    Foi adotado um banco de dados na nuvem para sustentar os dados da aplicação com conexão através da Wallet oracle;
  <br><br>
  
- Maven: 
  <br>  
    Utilizado para versionar e gerenciar as bibliotecas, assim facilitando a todos os desenvolvedores e usuários a utilizar o
  código mais atualizado no momento, principalmente na manutenção de bibliotecas Java utilizadas, algo que durante o processo 
  e na instalação do código final facilita o uso do mesmo;
  <br><br>
  

<h5>Frontend: </h5>

- Vue.js: 
  <br>
    Todo o visual e design da página web foram feitas utilizando essa tecnologia, isso inclue os relatórios e criação de laudos;
  <br><br>
- TypeScript:
  <br>
    Lógica das páginas, seja restrições das mesmas, preenchimentos ou a filtragem dos dados selecionados pelos 
  usuários e para tal a conexão e utilização das APIs criadas em java/springboot;
  <br>



<h4>Contribuições individuais</h4>
<details>
<summary>Backend </summary>
  <details>
<summary>Api Rest </summary>
	
  <p><br>
  	- Usando spring boot, criei as api's a serem consumidas, tanto as de criação dos laudos e as de selecionar valores dos 
	clientes e seus laudos e já registrados;
	<br>
	Exemplo:

    * @RestController
@RequestMapping(value = "/setor")
public class SetorController {
     @Autowired
     private ISetorService service;

     @GetMapping
     public List<Setor> buscarTodosSetores() {
          return service.buscarTodosSetores();
     }

     @PostMapping
     public Setor novoSetor(@RequestBody Setor setor) {
          return service.novoSetor(setor);
     }

     @GetMapping(value = "/{setor}")
     public Setor buscarPorId(@PathVariable("setor") Long id) {
          return service.buscarPorId(id);
     }
   
}

Neste exemplo utilizei um método get e post para receber os dados vindos do frontend. Como o frontend envia os dados num formato 
	json porém o vue.js envia os seus objetos e atributos de acordo com o banco, assim como estão feitas as entidades no backend. 
		No caso do método get/setor/{setor} um objeto do tipo setor está sendo recebido pela api e se usa o parâmetro ID para a pesquisa
	presente no service utilizado(buscar o registro com o id em específico);
		Ja o método post /setor é utilizado para receber o objeto setor com os paramêtros inseridos no frontend com o intuito de criar um 
	novo registro de setor(criar um novo setor para a aplicação);
		<br><br>
  O método get /setor seleciona todos os registros de setores;
  </p>
  </details>
   </details>
	<details>
   <summary> Frontend </summary>
  <details>
	<summary> Requisição das api's rest </summary>
	  - Exemplo de requisição Rest que consome a api do backend SpringBoot
  
		//Função para buscar os setores do banco
		async function buscarSetor() {
		  try {
		    const response = await axios.get('setor')
		    SelectionSection.value = response.data
		  } catch (error) {
		    console.error('Error fetching servico:', error)
		  }  
		}
  
  <br>
  <p> Nessa função estou consumindo a rota '/setor' que retorna um objeto com a lista de setores cadastrados; </p>
  </details>
	<details> 
		<summary> Vue.js </summary>
					<div>
			//Exemplo de uso da requisição no Vue.js
   			<br>
					
			  // <label/>Setor: </label>
			   // </select class="setor" id="setor" v-model="setor" @change="getSetor()">
			      </option v-for="s in setores" :key="s.id" v-bind:value="s.id"
			      >{{ s.nome}}</option>
			    // </select>
		
					// </div>
	      
<br><br>
<p> Utilizando do framework Vue.js foi possível armazenar a lista de setores para que sejam vizualidos 
na view do projeto utilizando o v-model, no caso de uso acima aparecem os setores para serem 
selecionados dentro de um html select, que ao selecionar através da anotação @change salva o 
ID do setor em questão para atualizar o registro no banco de dados</p>
</details>
</details>
  
 <h4>Aprendizado Efetivo:</h4>

  <summary>Requisição Rests:</summary>
  - Como consumir e utilizar uma api rest através do envio de um corpo de requisição adequado e como utilizar as 
  respostas foi um dos principais aprendizados;
<br><br>
 <summary>Vue.js:</summary>
	-O framework possibilitou o uso de routers, ou seja, dentro da mesma view é possível adicionar múltiplas 
 interfaces para o usuário;
 	- O uso de constantes diretamente no html através do v-model;
<br><br>
<summary>Conexão de banco de dados através de Wallet:</summary>
	-Utilizamos a wallet no repositório para que sem configurações extensas no application properties a conexão
 com o banco de dados fosse possível em qualquer máquina que a possuir.
 <br><br>
<summary>Spring Security: </summary>
	- Utilizando o security, validações de nível de usuário na aplicação foi possível ao adicionar a senha 
 criptografada em hash e separando os uuários por nível de acesso.
 <br><br>
 <summary>Spring e JPA: </summary>
 	- A função save() funciona tanto pra o Insert quanto pra um Update, ou seja, um objeto que não existe não 
  vai ter ID, logo é um novo registro. Agora um objeto com um ID existente substituirá os valores registrados no
  banco pelos atributos que ele contém se baseando no ID para realizar o update(where do update é o próprio ID do
  objeto em questão), isso é feito automaticamente na função save() do spring.
  presentes nele
  

  
