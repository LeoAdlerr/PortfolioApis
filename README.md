# Portfólios dos projetos API's(Aprendizagem por Projetos Integradores) FATEC Jessen Vidal

<h2> Leonardo Adler da Silva </h2>

  Olá, sou Leonardo Adler da Silva
estudante de Banco de Dados na Fatec Jessen Vidal, na qual tive a experiência de utilizar
metodologias ageis e diversas tecnologias nos projetos abaixo: 

### 1º Semestre (Fatec) : * [Link para portfólio 1º Semestre Python](https://github.com/LeoAdlerr/PortfolioApis/tree/main/1Semestre) 

### 2º Semestre (DomRock): * [Link para portfólio 2º Semestre Java](https://github.com/LeoAdlerr/PortfolioApis/tree/main/2Semestre)

### 3º Semestre (IACIT): * [Link para portfólio 3º Semestre Java - SpringBoot](https://github.com/LeoAdlerr/PortfolioApis/tree/main/3Semestre)

### 4º Semestre (JAIA): * [Link para portfólio 4º Semestre SpringBoot - Vue.JS](https://github.com/LeoAdlerr/PortfolioApis/tree/main/4Semestre)

## Feito por Leonardo Adler da Silva




<h3> Em 2021-2 foi trabalhado um projeto API com cliente interno(professores da Fatec) </h3> 

* [Video Apresentação do projeto](https://www.youtube.com/watch?v=0aUKWEjipQQ)

<br><br>
 
* [Link para o Repositório](https://github.com/LeoAdlerr/Projeto-Integrador-2021-2-Grupo3/tree/main)

<h4> Visão e objetivo do projeto </h4>
      O projeto tem como objetivo desenvolver um programa que forneça e informe as estatísticas 
    através de gráficos dos dados relacionados a Covid-19 no estado de São Paulo. A ideia é criar
    um programa com sistema eficaz e simples no terminal.

<h4>Tecnologias utilizadas no Projeto</h4>

- Python:
	<br>
    Todas as análises e gráficos foram feitas a partir do código fonte em python e suas bibliotecas;
  <br><br>
  
- Bibliotecas: 
  <br>  
    	Pandas = Extração dos dados csv e transformações necessárias além do dataframe ser criado a partir
  dessa bibliotecla;
  <br>
	Matplotlib = Com as análises feitas utilizando o pandas essa biblioteca utiliza-se dos dataframes
  transformados através das análises e filtros para gerar os gráficos;
  <br>
  	Unidecode = Usado para formatações e tipagens de valores que o pandas não faz; 
  <br><br>
  
<h4>Contribuições individuais</h4>
  <details>
<summary> Extração dos dados </summary>
	
  <p><br>
  	- Usando a lib pandas foi possível extrair os dados csv e adiciona-los num dataframe
  assim possibilitando as transformações e manipulações necessárias;
	  <br>
* [Exemplo de Extração]
	  
	  co = pd.read_csv('caso_full.csv')
Neste exeplo utilizei a função read_csv do pandas para gerar meu DataFrame; 
  </p>
  </details>
	  
	  
  
<details>
<summary>Manipulação de dados</summary>
<p><br><br>
	Filtrando apenas os dados de SP(São Paulo)
	<br><br>  	
  Com o código abaixo foi possível manipular o dataframe para apenas os dados do estado de São Paulo;
	
	  colSP = co.loc[co["state"] == ("SP")]
</p>
</details>
	
<details>
<summary> Utilização de laços </summary>
<p><br> <br>
	No exemplo em questão, através de um laço foi possível gerar um mecanismo de escolhas das análises desejadas;
	<br>


        plpl = str("")
        while plpl !=("90"):
            print('''[ 1 ] dado específico
                        [ 2 ] comparações
                            [ x ] Voltar a escolha das cidades/estado''')
            F = input("Digite a sua escolha: ")

            if F == "1":
                print("escolha entre os dados disponíveis(abaixo):")
                print('''[ 1 ] Casos confirmados
                                             [ 2 ] Óbitos confirmados''')
                FF = input("Digite a sua escolha: ")

                if FF == "1":

                    print('''\033[0;35mEscolha uma das opçoes
                                                [ 1 ] data expecifica
                                                [ 2 ] última data disponível
                                                [ 3 ] Ano de 2020
                                                [ 4 ] Ano de 2021
                                                [ 5 ] 1ºSemestre 2020
                                                [ 6 ] 2ºSemestre 2020
                                                [ 7 ] 1ºSemestre 2021
                                                [ 8 ] 2ºSemestre 2021
                                                [ 9 ] Range inputável\033[m''')
                    esc = str("")

                    while esc != ("1", "2", "3", "4", "5", "6", "7", "8"):

                        esc = str(input('Digite a sua escolha(1, 2, 3, 4, 5 ,6, 7, 8, 9): '))

                        if esc == "1":
                            dt2 = input("\033[0;35mDigite a data nesse formato(ano-mês-dia)ex:yyyy-mm-dd:\033[m")

                            colDT2 = colSP1.loc[colSP1["date"] == dt2]

                            while colDT2.empty:
                                print("\033[0;31mData não encontrada\n Digite novamente\033[m")
                                dt2 = input("Digite a data nesse formato(ano-mês-dia)ex:yyyy-mm-dd:")
                                colDT2 = colSP1.loc[colSP1["date"] == dt2]

                            colDT2 = colDT2.drop("state", axis=1)
                            colDT2 = colDT2.drop("place_type", axis=1)

                            plt.bar(colDT2['date'], colDT2['new_confirmed'], label='Casos', color='g', ls='--',
                                    lw='2')  # Caso queira grafico de barras colocar - plt.bar()
                            plt.legend(loc=2, fontsize='15')  # Personalização da legenda
                            plt.ylabel('Casos Confirmados')  # Nome do Eixo Y
                            plt.xlabel('Data')  # Nome do Eixo X
                            plt.title('Gráfico situação de casos por dia')  # Título do gráfico
                            xxxx = colDT2.sum()
                            print("Casos de Covid no dia:")
                            print(xxxx["new_confirmed"])
                            plt.show()
                            break
</p>
</details>
	
<details>
<summary> Geração de gráficos: </summary>
<p><br><br>
	A biblioteca matplotlib possibilou a criação de gráficos para as análises e no exemplo
trago um gráfico de casos confirmados de covid na data especificada pelo usuário;
	<br>
	
			plt.bar(colDT2['date'], colDT2['new_confirmed'], label='Casos', color='g', ls='--',
			    lw='2')  # Caso queira grafico de barras colocar - plt.bar()
		    plt.legend(loc=2, fontsize='15')  # Personalização da legenda
		    plt.ylabel('Casos Confirmados')  # Nome do Eixo Y
		    plt.xlabel('Data')  # Nome do Eixo X
		    plt.title('Gráfico situação de casos por dia')  # Título do gráfico
		    xxxx = colDT2.sum()
		    print("Casos de Covid no dia:")
		    print(xxxx["new_confirmed"])
	    		plt.show()
<br>
</p>
</details>
  
 <h4>Aprendizado Efetivo:</h4>

  <summary> Extração e Análise de dados :</summary>
  -  A biblioteca pandas foi de suma importância, a manipulação dos dados para a gerção de análises diversas foi o principal aprendizado.
<br>	<br>
<summary> Laços e lógica de programação:</summary>
	- A implementação de laços como while e for foram o alicerce da lógica desse projeto com isso as diversas análises possíveis estavam 
 dentro de um laço e sempre podendo voltar ao laço anterior ou finalizar as escolhas através dos if;
<br><br>
 <summary> Vizualização das análises:</summary>
	- Toda a análise só gera valor se o cliente entender o que foi analisado, ou seja, através dos gráficos gerados pelas escolhas de análise
 seja por dia, período ou o tipo de informação solicitada(casos de covid, óbitos, etc) o usuário pode entender o que ele deseja de forma mais clara
 quantitativamente e nos períodos selecionados;
<br><br>




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


  
