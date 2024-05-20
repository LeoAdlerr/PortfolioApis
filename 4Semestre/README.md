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
<br>
-Segurança de Logins e geração de relatórios através do Spring Security;
  <br>
- Oracle Cloud(AWS): 
  <br><br>
    Foi adotado um banco de dados na nuvem para sustentar os dados da aplicação;
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
		O método get /setor seleciona todos os registros de setores;
  </p>
  </details>

  <details>
	<summary> Routers </summary>
  </details>
  
 <h4>Aprendizado Efetivo:</h4>

  <summary>Api's Rest:</summary>
  - Foi o principal aprendizado, pois através desse entendimento é possível criar diversos tipos de aplicativos
  web, principalmente aqueles que necessitam de algum mecanismo de busca ou até para mostrar dados, seja em forma de gráficos como foi o nosso
		caso ou de diversas outras maneiras.
    No caso, a conexão http através dos links, os tipos de retorno e como utiliza-los(enviando e recebendo JSON's), onde utilizamos POST, GET,
    PUT entre outros tipos de requests que possibilitaram a conexão entre o Banco de Dados e o Front do projeto;
<br>	<br>
<br><br>
 <summary>Polimorfismo:</summary>
	-Ao separar as classes em Interfaces, Services, Entitys(Repositories) e Controllers, foi possível herdar funcionalidades de classes para no final controla-las(tendo separado cada parte do processo), assim selecionando de acordo com a necessidade e economizando linhas de código;
<br><br>
<summary>Persistência:</summary>
	-Utilizando a orientação a objeto/polimorfismo, criamos passos que começam desde o download dos CSVs com os dados meteorológicos, tratamento desses arquivos e inserção definitiva utilizando esses dados no banco, isso tendo em vista que é uma quantidade massiva de informações, ou seja, todos os passos necessários para tal foram implementados.

  

  
