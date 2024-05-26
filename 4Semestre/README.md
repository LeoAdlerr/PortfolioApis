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
  

  
