
<h3> Em 2022-1 foi trabalhado um projeto API com o parceiro acadêmico DomRock </h3> 
 
* [Link para o Repositório](https://github.com/DatatechOffice/datatech_api)

<h4> Visão e objetivo do projeto </h4>
    O desafio consiste na gestão de ativação de clientes na plataforma Dom Rock. Precisamos de uma 
solução que seja orientada a entrada de dados de parâmetros e variáveis de cada cliente para alocar 
recursos na plataforma Dom Rock, entrada de dados e estimativa de consumo de recursos (baseado 
em volume de dados de cliente, quantidade de usuários e outros) e gere relatórios e consultas, mas, 
principalmente, tenha a base de dados modelada adequadamente para futuras integrações com 
outros sistemas.
	Para realizar o deafio, foi necessária a Criação de interfaces para cada etapa do programa visando 
 facilitar a ativação delas e dos cadastros posteriormente, além de tornar o processo visível aos clientes.

<h4>Tecnologias utilizadas no Projeto</h4>

- Java: 
  <br>
    A linguagem de programação utilizada com as lógicas para inserção, selecionar, deletar e excluir.
  Assim conectando o banco de dados a aplicação Desktop;
  <br><br>
  - SqlServer: 
  <br>
    Foi utilizado um banco na nuvem azure(SqlServer) onde os dados de login e dos pedidos dos clientes foram
    armazenados;
  <br><br>
  - JavaSwing: 
  <br>
    Todo o visual e design da aplicação foi feita usando essa tecnologia, desde a tela de login até a tela gold;
  <br><br>
- Maven: 
  <br>  
    Utilizado para versionar e enviar o código no Git, assim facilitando a todos os desenvolvedores e usuários a utilizar o
  código mais atualizado no momento, principalmente na manutenção de bibliotecas Java utilizadas, algo que durante o processo 
  e na instalação do código final facilita o uso do mesmo;
  <br><br>
  
<h4>Contribuições individuais</h4>
<details>
<summary> Classes DAO de Conexão com BD </summary>
	
  <p><br>
  	- Foi criada uma classe DAO chamada ConnectionManager, ela tem o objeto com conexão pro Banco de Dados e que por consequência
  todas as demais classes Dao irão utilizar, assim não tendo a necessidade de abrir uma nova conexão a cada evento da aplicação:
<br>
					* [classe ConnectionManager exemplo]
	  

	  public static Connection getConnection() throws SQLException { return
	  DriverManager.getConnection(
	  "jdbc:sqlserver://XXXXXX.DDDDDD.WWWWWW.net;databaseName=DDDD;user=SSSSSS;password=***********"
	  ); }
<br>
  </p>
  </details>
  <details>
<summary> Classes DAO dos Objetos </summary>
	
  <p><br>
  	- Foi criada uma classe DAO chamada DaoCliente, onde todo evento que envolva o banco de dados na tabela/entidade Cliente 
	  é realizada:
<br>
					* [classe DaoCliente exemplo]
	  
								public void criarCl(Cliente c1) {
								this.c1=c1;
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
<br>
    Neste exemplo o método criarCl() recebe um objeto da entidade Cliente que por sua vez utiliza dos gets presente nos atributos
do objeto da Classe Cliente para criar um novo registro na tabela cliente com os valores especificados na view. 
  </p>
  </details>
	  
	  
  
<details>
<summary> Modelagem Relacional </summary>
<p><br><br>
	Foi gerado uma modelagem relacional para satisfazer a necessidade de cadastrar clientes e seus pedidos/produtos
	<br><br>
 *[Modelagem da aplicação]
  	
![image](https://github.com/LeoAdlerr/PortfolioApis/assets/88751032/5c21e53a-fb14-468f-8472-d8ed36985de5)

</p>
</details>
	
<details>
<summary>Orientação a Objeto e classes que representam algo na vida real</summary>
<p><br> <br>
	No exemplo em questão represento a tabela cliente, que contém os valores que serão cadastrados pela aplicação no banco de dados
	, ou seja, os valores que representam esse cliente na vida real;
		<br>
	
		//Classe
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
</p>
</details>
	
  
 <h4>Aprendizado Efetivo:</h4>

  <summary> Orientação a Objeto :</summary>
  - Foi o principal aprendizado, criando classes que representassem as tabelas do banco de dados com os mesmos atributos uma tarefa de 
mapear e representar os registros na aplicação se tornou muito mais prático;
<br>	<br>
<summary> MVC(Model, View, Controller):</summary>
	- Com classes para representar a modelagem do BD, separadas das classes de visão e conexão com o Banco, cada tarefa pode se tornar
 muito mais específica além da aplicação ser mais fácil de ser compreendida por qulaquer desenvolvedor, ja que cada parte do código segue 
 o seu padrão;
<br><br>
 <summary> Modelagem Relacional:</summary>
	-Para representar as algo na vida real foi necessário criar uma modelagem relacional e nesse projeto foi algo imprescindível pois os
 dados de uma visão dependiam dos valores inseridos na anterior, inclusive tendo a possibilidade de uma visão que podiam ter registros multiplos
 da anterior para o mesmo cliente (relacionamento 1,N ou um pra muitos) e outras que apenas um registro era possível(relacionamento 1,1 ou um pra um);
<br><br>


  
