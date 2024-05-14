<h2> Leonardo Adler da Silva </h2>

  Olá, sou Leonardo Adler da Silva
estudante de Banco de Dados na Fatec Jessen Vidal, na qual tive a experiência de utilizar
metodologias ageis e diversas tecnologias.  

<h3> Em 2022-2 foi trabalhado um projeto API com o parceiro acadêmico IACIT </h3> 
* [Video Apresentação do projeto](https://github.com/DatatechOffice/Api_Iacit)
 https://www.youtube.com/watch?v=0aUKWEjipQQ
* [Link para o GitHub](https://github.com/DatatechOffice/Api_Iacit)

<h4> Visão e objetivo do projeto </h4>
    Desenvolver um sistema web, onde fosse possível realizar a extração e tratamento
  de dados meteorológicos através do site INEP fornecido pelo parceiro, além da persistência 
  dos mesmos e por fim a visualização dos dados de forma que decisões pudessem ser realizadas,
  no caso foram utilizado gráficos e a filtragem dos dados pelo usuário para tal.

<h4>Tecnologias utilizadas no Projeto</h4>

- HTML, CSS e Bootstrap: 
  <br>
    Todo o visual e design da página web foram feitas utilizando essas tecnologias, isso inclue os gráficos 
  com os dados meteorológicos auxiliando-se das lógicas do Javascript para tal;
  <br><br>
- JavaScript:
  <br>
    Lógica das páginas, seja restrições das mesmas, preenchimentos ou a filtragem dos dados selecionados pelos 
  usuários e para tal a conexão e utilização das APIs criadas em java/springboot;
  <br><br>
- Java e SpringBoot:
  <br><br>
    Primeiramente foram feitas rotinas para persistir a base de dados meteorológicos; 
    Depois a criação  das Apis Rest conectando o banco de dados que contém os dados meteorológicos com as páginas, 
  para tal foram criadas pesquisas aliadas a lógicas para buscar e filtrar os dados e assim enviando os resultados
  em formato JSON para que possam ser tratados pelo JavaScript;
  <br><br>
- Python: 
  <br><br>
    Uma rotina para captação dos dados em csv fornecidos pelo cliente foi criada, para assim criar um csv com os  
  valores de todos os períodos agregados e assim podendo envia-los num formato onde fosse possível persisti-los usando
  o java;
  <br><br>
- PostgreSQL: 
  <br><br>
    Foi o banco de dados de preferência da empresa contratante e o utilizado para armazenar os dados meteorológicos de 
  uma forma de uma forma que fosse possível utiliza-los num programa, além de traze-los num formato e tipo que 
  falicitassem o uso;
  <br><br>
  
- Maven: 
  <br>  
    Utilizado para versionar e enviar o código no Git, assim facilitando a todos os desenvolvedores e usuários a utilizar o
  código mais atualizado no momento, principalmente na manutenção de bibliotecas Java utilizadas, algo que durante o processo 
  e na instalação do código final facilita o uso do mesmo;
  <br><br>
  
<h4>Contribuições individuais</h4>
  <details>
<summary>Api Rest </summary>
	
  <p><br>
  	- Usando spring boot, criei as api's a serem consumidas, nas quais conectei com o banco sql para buscar os dados 
  filtrados pelo frontend, foi pensado em criar uma lógica que contemple quaisquer pesquisas feitas, além
  do crud com as telas de Login;
	  <br>
    * [classe Controller exemplo]@Controller
public class TemperaturaController {

	@Autowired(required = true)
	private ServiceTemperatura temperaturaService;

	@PostMapping(value = { "/temperatura" }, consumes = MediaType.APPLICATION_JSON_VALUE)
	public ResponseEntity<List<Temperatura>> postFiltroPorData(@RequestBody FilterDataVo data) throws ParseException {
		
		List<Temperatura> listTemperatura = temperaturaService.getByFilter(data.getEstacao(), data.getDataInicio(), data.getDataFim());
		
		return listTemperatura != null && listTemperatura.size() > 0 ? new ResponseEntity<List<Temperatura>>(listTemperatura, HttpStatus.CREATED)
				: new ResponseEntity<List<Temperatura>>(listTemperatura, HttpStatus.BAD_REQUEST);

	}
}    
    Neste exemplo utilizei um método post para receber os dados vindos do frontend, no caso em formato JSON. Para receber esse json foi 
  necessário criar uma classe(FilterDataVO) que tivesse um modelo e atributos equivalentes aos vindos do JS.
    Entra os dados no método vindos de um service que foi feita a inserção de dependência na classe controller e após a resposta, dependendo
  do retorno ou não da função(getByFilter), existe um ternário para dar uma resposta que no caso pode ser um BadRequest(se não houver um
  retorno)  ou Created(caso haja um retorno). 
  </p>
  </details>
	  
	  
  
<details>
<summary>Manipulação de dados
- Na persistência</summary>
<p><br><br>
	Scripts em java para popular o banco com os dados vindos do csv
	<br><br>
 *[Classe regiaoService]
  	
  Nesse trecho primeiramente recebo os dados vindos do csv referentes aos estados e como são diversas linhas
	  com o mesmo valor seguidas, criei uma lógica que quando um valor fosse inserido(for), só teria uma inserção 
	  novamente quando houvesse uma mudança, pois só queriamos uma instância de cada Estado nas tabelas, utilizando 
	  um objeto com os valores em seus atributos utilizamos o springBoot para inserir cada instância na respectiva tabela,
	  usando o comando .save;
	
	  public void insBancoService
	  (ArrayList<String> regEstN,
	  ArrayList<String> regEstC,
	  ArrayList<String> regEstLA, 
	  ArrayList<String> regEstLO, 
	  ArrayList<String> regEstAL, 
   	  ArrayList<String> regEstD, 
	  ArrayList<String> etd) 
		int ii = regEstC.size();
		for (int i = 1; i < ii; i++) {
			String estNome = regEstN.get(i);
			String estC = regEstC.get(i);
			String latitude = regEstLA.get(i);
			String longitude = regEstLO.get(i);
			String altitude = regEstAL.get(i);
			String dataFundacao = regEstD.get(i);
			String estadoS = etd.get(i);

			if (i - 1 >= 0 && regEstC.get(i - 1) != estC) {
				Estado estado = new Estado();
				estado = serviceEstado.returnEstado(estadoS);
				Estado estadoID = new Estado(estado.getEtdId());
				Estacao estacao = new Estacao(estadoID, estC, BigDecimal.valueOf(Double.parseDouble(longitude)),
						estNome, Timestamp.valueOf(dataFundacao + " 00:00:00"),
						BigDecimal.valueOf(Double.parseDouble(latitude)),
						BigDecimal.valueOf(Double.parseDouble(altitude)));
				estacaoRepository.save(estacao);
			} else {
				continue;
			}
    };
	</p>
</details>
	
<details>
<summary>Orientação a Objeto e classes que representam algo da vida real</summary>
<p><br> <br>
	No exemplo em questão represento a Radiação globlal das cidades em questão, que contém o horário da coleta e o valor da radiação no momento da coleta do dado;
	<br>
@Entity(name = "radiacao_global")
@Table(name = "radiacao_global")
@Getter
@Setter
@NoArgsConstructor
@Component
public class RadiacaoGlobal {
	public RadiacaoGlobal(Estacao estCodigo, Timestamp dataHora, BigDecimal valor) {
		this.estCodigo=estCodigo;
		this.dataHora=dataHora;
		this.valor=valor;
	}
	
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name= "rag_id")
    private Integer ragId;

	@Column(name= "rag_radiacao_global")
    private BigDecimal valor;

	@Column(name= "rag_data_hora")
    private Timestamp dataHora;

	@ManyToOne
	@JoinColumn(name = "est_codigo", referencedColumnName = "est_codigo")
	private Estacao estCodigo;
}
		</p>
	</details>
	
<details>
<summary>Polimorfismo</summary>
<p><br><br>
	Com a utilização de Interfaces do Hibernate, criamos uma possibilidade de utilizar os atributos para
comunicar colunas e tabelas do banco de dados com as classes que representam cada respectiva entidade;
	<br>
	@Repository
public interface EstadoRepository extends JpaRepository<Estado, Integer> {
	@Query(value = "SELECT * FROM estado WHERE etd_unidade_federativa = ?1", nativeQuery = true)
	public Estado selectBySigla(String etd);

	@Query(value = "SELECT * FROM estado", nativeQuery = true)
	public List<Estado> selectEstado();
	}
</p>
</details>
  
 <h4>Aprendizado Efetivo:</h4>

  <summary>Api's Rest:</summary>
  - Foi o principal aprendizado, pois através desse entendimento é possível criar diversos tipos de aplicativos
  web, principalmente aqueles que necessitam de algum mecanismo de busca ou até para mostrar dados, seja em forma de gráficos como foi o nosso
		caso ou de diversas outras maneiras.
    No caso, a conexão http através dos links, os tipos de retorno e como utiliza-los(enviando e recebendo JSON's), onde utilizamos POST, GET,
    PUT entre outros tipos de requests que possibilitaram a conexão entre o Banco de Dados e o Front do projeto;
<br>	<br>
<summary>Orientação a Objeto:</summary>
	-As classes da pasta Entity, com auxilio do hibernate, são objetos que representam as tabelas do banco de dados e consequentemente suas representações de algo na vida real, como a classe Temperatura que representa as temperaturas de cada cidade e a classe Região que representa as regiões geográficas do Brasil(Sul, Centro-Oeste, etc);
<br><br>
 <summary>Polimorfismo:</summary>
	-Ao separar as classes em Interfaces, Services, Entitys(Repositories) e Controllers, foi possível herdar funcionalidades de classes para no final controla-las(tendo separado cada parte do processo), assim selecionando de acordo com a necessidade e economizando linhas de código;
<br><br>
<summary>Persistência:</summary>
	-Utilizando a orientação a objeto/polimorfismo, criamos passos que começam desde o download dos CSVs com os dados meteorológicos, tratamento desses arquivos e inserção definitiva utilizando esses dados no banco, isso tendo em vista que é uma quantidade massiva de informações, ou seja, todos os passos necessários para tal foram implementados.

  

  
