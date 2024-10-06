<!-- Portfolio Sections -->
<div id="topo">
    <h1>Welcome to My API Project Portfolio (Learning through Integrative Projects) by FATEC São José dos Campos - Jessen Vidal</h1>
</div>

<h2><a href ="https://github.com/LeoAdlerr/PortfolioApis/blob/main/README.md"> PT/BR Portfolio </a><h2>

## Leonardo Adler da Silva

Hello, I am **Leonardo Adler da Silva**, a Database student at FATEC São José dos Campos - Jessen Vidal. Throughout my academic journey, I have had the opportunity to work with agile methodologies and various technologies, resulting in exciting projects that I share below.

### 🚀 Projects by Semester

<table style="width:100%; border-collapse: collapse; margin-top: 20px;">
    <thead>
        <tr>
            <th style="border: 1px solid #ccc; padding: 10px; text-align: left;">Project</th>
            <th style="border: 1px solid #ccc; padding: 10px; text-align: left;">Description</th>
            <th style="border: 1px solid #ccc; padding: 10px; text-align: left;">Technologies</th>
            <th style="border: 1px solid #ccc; padding: 10px; text-align: left;">Client</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><a href="#portfolio1Covid">1st Semester Python (Fatec/Internal)</a></td>
            <td>Development of a program that presents statistics on Covid-19 in SP, helping the population understand the pandemic through accessible graphs and data.</td>
            <td>Python</td>
            <td>Fatec</td>
        </tr>
        <tr>
            <td><a href="#portfolio2DomRock">2nd Semester Java Desktop (DomRock)</a></td>
            <td>Development of a solution for managing customer activation on the Dom Rock platform, allowing data entry on parameters and variables for each client, with data modeling for future integrations and report generation.</td>
            <td>Java, Swing, SQL Server</td>
            <td>DomRock</td>
        </tr>
        <tr>
            <td><a href="#portfolio3IACIT">3rd Semester Java - SpringBoot (IACIT)</a></td>
            <td>Development of a system to automate the import and storage of meteorological data, enabling the generation of customized reports and reducing time and resource waste in meteorological consulting.</td>
            <td>Java, SpringBoot, PostgreSQL</td>
            <td>IACIT</td>
        </tr>
        <tr>
            <td><a href="#portfolio4Jaia">4th Semester Vue.JS - SpringBoot (JAIA)</a></td>
            <td>Development of a system to control anomalies in Building Inspection Reports, managing preventive and corrective maintenance to ensure the safety and quality of properties.</td>
            <td>Vue.js, SpringBoot, Oracle Cloud</td>
            <td>JAIA</td>
        </tr>
        <tr>
            <td><a href="#portfolio5Tecsus">5th Semester Node.js - PowerBi (TECSUS)</a></td>
            <td>Development of a web dashboard for analyzing energy and water bills, aiming to optimize contracts and reduce costs for TecSUS's client companies.</td>
            <td>Node.js, Power BI, ETL, MySQL</td>
            <td>TECSUS</td>
        </tr>
        <tr>
            <td><a href="#portfolio6SPCGrafeno">6th Semester Artificial Intelligence - Node.js (SPC Grafeno)</a></td>
            <td>Development of innovative financial products using machine learning to analyze the reliability of endorsers and predict financial asset trends.</td>
            <td>Node.js, Machine Learning, AI, PostgreSQL, Railway</td>
            <td>SPC Grafeno</td>
        </tr>
    </tbody>
</table>

#### Made with enthusiasm by Leonardo Adler da Silva

<div id="portfolio1Covid">
	<h2>In 2021-2, an API project was developed with an internal client (Fatec)</h2>
</div>

* [Link to the Repository](https://github.com/LeoAdlerr/Projeto-Integrador-2021-2-Grupo3)

  <strong>Project Overview:</strong> This project aims to develop a program that provides and informs statistics through graphs of data related to Covid-19 in the state of São Paulo. The idea is to create an effective and simple program in the terminal.<br><br>
  <strong>Project Relevance:</strong> The project is relevant to society, as it helps people understand the proportions of the pandemic in recent times. By showing precise data on the number of infected individuals and deaths caused by Covid-19, it is crucial for the population to be aware of this information and, based on these data, draw their conclusions about the disease and the effectiveness of measures taken in the state of SP.<br><br>
  <strong>Objectives:</strong> Collect necessary data to create the program with graphs, including the aggregate of individuals who have died and cases of people who contracted COVID-19. The program is designed to be accessible and simple, comparing precise data from the region and the user’s preferred date.
           
## Technologies Used

- **Python:** A versatile programming language that is well-suited for data analysis and visualization tasks due to its simplicity and readability, making it an ideal choice for rapid development.

- **Pandas:** A powerful data manipulation library that provides data structures and functions needed to efficiently handle and analyze structured data, allowing for easy filtering, aggregation, and cleaning of datasets.

- **Matplotlib:** A comprehensive plotting library that enables the creation of static, animated, and interactive visualizations in Python. It is used to produce publication-quality graphs and provides a variety of customization options for visual representation of data.

## My Contributions
During the development of the project, I actively participated in the following activities:
- **Data Collection and Manipulation:** I used the Pandas library to extract relevant data from the CSV file, filtering specific information about the state of São Paulo.
  <details>
    <summary>Example of Data Collection and Manipulation Code</summary>
    <pre>
    <code>
    import pandas as pd

    # Load the data
    df = pd.read_csv('caso_full.csv')

    # Filter data for the state of SP
    df_sp = df[df['estado'] == 'SP']
    </code>
    </pre>
  </details>
- **Graph Creation:** I implemented visualizations using Matplotlib to present the statistics clearly and intuitively, facilitating the user's understanding of the data.
  <details>
    <summary>Example of Graph Creation Code</summary>
    <pre>
    <code>
    import matplotlib.pyplot as plt

    # Confirmed cases graph
    plt.plot(df_sp['data'], df_sp['casos_confirmados'])
    plt.title('Confirmed Covid-19 Cases in SP')
    plt.xlabel('Date')
    plt.ylabel('Confirmed Cases')
    plt.show()
    </code>
    </pre>
  </details>
- **Program Interactivity:** I structured a menu system that allows the user to select different analysis options, making the experience interactive and dynamic.
  <details>
    <summary>Example of Interactivity Code</summary>
    <pre>
    <code>
    def menu():
        print("1. View data")
        print("2. Generate graph")
        choice = input("Choose an option: ")
        return choice

    # Example of calling the menu
    option = menu()
    </code>
    </pre>
  </details>
  
## Effective Learnings
This project provided me with valuable experience in programming and data analysis. I learned:
- **Use of Python Libraries:** The importance of Pandas and Matplotlib libraries in data manipulation and visualization.
- **Control Structures:** The use of loops and conditionals to create an interactive interface.
- **Data Analysis:** How to transform raw data into useful and meaningful information for the audience.

## Final Considerations
This project marked my first contact with programming and data analysis. Even as a beginner, it was gratifying to see the creation of a tool that not only gathers information but also provides real and relevant insights to users. The experience gained was essential for my personal and professional development, motivating me to continue learning and improving my skills in technology and data science.

<!-- Navigation Links -->
<a href="#topo">Back to Top</a>

<br><br>

<div id="portfolio2DomRock">
	<h2>In 2022-1, an API project was developed with the academic partner DomRock</h2> 
</div>

 
# Customer Activation Management Project - Dom Rock

* [Link to the Repository](https://github.com/DatatechOffice/datatech_api)

## Project Vision and Objective
The challenge involves managing customer activation on the Dom Rock platform. We needed a solution focused on entering parameters and variables for each customer to allocate resources on the Dom Rock platform, estimate resource consumption (based on customer data volume, number of users, and others), and generate reports and queries. Most importantly, the database had to be appropriately modeled for future integrations with other systems. To achieve this, it was necessary to create interfaces for each stage of the program, aiming to facilitate their activation and subsequent registrations, while also making the process visible to customers.

## Technologies Used in the Project
<ul>
  <li><strong>Java:</strong> 
    <br>The programming language used for the logic of inserting, selecting, deleting, and excluding data, thus connecting the database to the Desktop application.
  </li>
  <li><strong>SqlServer:</strong> 
    <br>A cloud database (SqlServer) on Azure was used to store login data and customer requests.
  </li>
  <li><strong>JavaSwing:</strong> 
    <br>All visual and design aspects of the application were created using this technology, from the login screen to the gold screen.
  </li>
  <li><strong>Maven:</strong> 
    <br>Utilized for versioning and pushing code to Git, making it easier for all developers and users to utilize the most up-to-date code, especially in maintaining used Java libraries, facilitating the installation of the final code.
  </li>
</ul>

## Individual Contributions

<details>
<summary>DAO Connection Classes</summary>
  <p><br>
    - A DAO class named ConnectionManager was created, which contains the object for the database connection and is utilized by all other DAO classes, eliminating the need to open a new connection for every event in the application:
    <br><br>
    * [ConnectionManager Class Example]
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
<summary>DAO Object Classes</summary>
  <p><br>
    - A DAO class named DaoCliente was created, where every event involving the database in the Client table/entity is executed:
    <br><br>
    * [DaoCliente Class Example]
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
            throw new RuntimeException("Error inserting data!", e);
        } finally {
            try {
                if (con != null)
                    con.close();
            } catch (SQLException e) {
                e.printStackTrace();
                throw new RuntimeException("Error closing connection", e);
            }
        }
    }
    </code></pre>
    In this example, the method criarCl() receives an object of the Client entity, which uses the getters present in the object's attributes to create a new record in the client table with the values specified in the view.
  </p>
</details>

<details>
<summary>Relational Modeling</summary>
  <p><br>
    A relational model was generated to meet the need for registering clients and their orders/products.
    <br><br>
    *[Application Modeling]
    <br><br>
	  <img src="https://github.com/LeoAdlerr/PortfolioApis/assets/88751032/5c21e53a-fb14-468f-8472-d8ed36985de5">  
  </p>
</details>

<details>
<summary>Object-Oriented Programming and Classes Representing Real-Life Entities</summary>
  <p><br>
    In this example, I represent the client table, which contains the values to be registered by the application in the database, meaning the values that represent this client in real life:
    <br><br>
    //Class
    <pre><code>
    public class Cliente {
        //Attributes
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

## Effective Learning

### Object-Oriented Programming:
- The main takeaway was creating classes that represent the database tables with the same attributes; this task of mapping and representing records in the application became much more practical.

### MVC (Model, View, Controller):
- With classes to represent the database modeling, separated from the view and database connection classes, each task became more specific, making the application easier to understand for any developer, as each part of the code follows its standard.

### Relational Modeling:
- To represent something in real life, it was necessary to create a relational model. In this project, this was essential, as the data from one view depended on the values inserted in the previous one, including the possibility of a view that could have multiple records from the previous one for the same client (1,N relationship or one-to-many) and others that only allowed a single record (1,1 relationship or one-to-one).

The key learnings include:
- **Importance of Communication:** Effective communication among team members and stakeholders was crucial for the project's progress and problem-solving.

- **Adaptation to Change:** The ability to adapt the project's scope and priorities in response to continuous feedback significantly improved the quality of the final product.

- **Agile Development:** The application of agile methodologies allowed for continuous delivery of features, ensuring the project remained aligned with client expectations.

## 💡 Final Considerations
The project was a rich experience in learning and collaboration. Throughout the development, we faced challenges such as defining system requirements and integrating different technologies, which were overcome with the collective effort of the team.

<!-- Navigation Links -->
<a href="#topo">Back to Top</a>

<br><br>

<div id="portfolio3IACIT">
	<h1>In 2023-1, an API project was developed with the academic partner IACIT</h1>  
</div>

* [Link to the Repository](https://github.com/DatatechOffice/Api_Iacit)

<h4>Project Vision and Objective</h4>
The goal was to develop a web system capable of extracting and processing meteorological data through the INEP website provided by the partner, as well as ensuring data persistence, ultimately allowing for data visualization to facilitate decision-making. To achieve this, graphs were implemented, along with user data filtering options.

<h4>Technologies Used in the Project</h4>

- **HTML, CSS, and Bootstrap:** 
  All the visual and design elements of the web page were created using these technologies, including the graphs that display meteorological data, enhanced by JavaScript logic.
  
- **JavaScript:**
  Used for page logic, including restrictions, data entries, and filtering of user-selected data, connecting to and utilizing the APIs created in Java/Spring Boot.
  
- **Java and Spring Boot:**
  Developed routines to persist meteorological data and create REST APIs that connect the database containing meteorological data with the web pages, allowing results to be sent in JSON format for processing by JavaScript.
  
- **Python:** 
  A routine was created to capture data in CSV format provided by the client, allowing the generation of a CSV file with aggregated values from all periods, enabling persistence using Java.
  
- **PostgreSQL:** 
  This was the preferred database of the contracting company, used to store meteorological data in a way that facilitated its use in a program and presented it in a format that made it easy to work with.
  
- **Maven:** 
  Used for versioning and pushing code to Git, making it easier for all developers and users to utilize the most updated code, particularly for maintaining the Java libraries used.

<h4>Individual Contributions</h4>

<details>
<summary>REST API</summary>
- Using Spring Boot, I created APIs to be consumed, connecting them to the SQL database to retrieve filtered data from the frontend. The logic was designed to accommodate any searches made, along with CRUD functionalities and login screens.

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
<summary>Data Manipulation - Persistence</summary>
- I developed Java scripts to populate the database with data from the CSV, ensuring that only one instance of each State was inserted into the tables.

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
<summary>Object-Oriented Programming and Real-World Class Representation</summary>
- The classes were structured to represent the Global Radiation of cities, with attributes reflecting the collection time and the radiation value.

<pre><code>
@Entity
public class RadiacaoGlobal {
    @Id
    private Long id;
    private String cidade;
    private LocalDateTime horarioColeta;
    private Double valorRadiacao;

    // Getters and Setters
}
</code></pre>
</details>

<details>
<summary>Polymorphism</summary>
- Using Hibernate interfaces, it was possible to map the columns and tables of the database with the classes representing each respective entity.

<pre><code>
public interface RadiacaoRepository extends JpaRepository<RadiacaoGlobal, Long> {
    List<RadiacaoGlobal> findByCidade(String cidade);
}
</code></pre>
</details>

<h4>Effective Learning:</h4>

<summary>REST APIs:</summary>
- This was the primary learning experience, allowing for the creation of various types of web applications that require search mechanisms or data presentation, such as graphs. The most important takeaway was understanding how to build a REST API using Spring Boot.

<summary>HTTP Protocol and REST APIs:</summary>
- I learned about the HTTP protocol and how it serves as the foundation for communication between client and server. REST APIs utilize HTTP methods (such as GET, POST, PUT, and DELETE) to perform operations on resources, allowing for data exchange in JSON format. This interconnection is fundamental for building web applications that efficiently communicate with the backend.

<summary>Object-Oriented Programming:</summary>
- The classes in the Entity folder, aided by Hibernate, represent the database tables and their correspondence to real-world entities.

<summary>Polymorphism:</summary>
- Separating classes into Interfaces, Services, Entities (Repositories), and Controllers facilitated the inheritance of functionalities and control over the process components, saving lines of code.

<summary>Persistence/ETL:</summary>
- Using object-oriented programming and polymorphism, we implemented the entire process from downloading CSVs with meteorological data, processing these files, and inserting them into the database, considering the massive amount of information.

<h4>Conclusion</h4>
The project developed in partnership with IACIT was an enriching experience, providing a deep understanding of API usage, data manipulation, and the implementation of efficient web solutions. Learning the Spring framework was crucial for structuring applications, enabling the development of robust and scalable systems, effectively aligning theory with practice.

<!-- Navigation links -->
<a href="#top">Back to Top</a>

<br><br>

<div id="portfolio4Jaia">
	<h2>In 2023-2, an API project was developed in partnership with JAIA</h2> 
</div>

* [Link to the Project Repository](https://github.com/Great-Pretender/GreatPretender-API)

<h4>Project Vision and Objectives</h4>

A system developed to control the status of a property, with results exported in a Building Inspection Report. It also manages preventive and corrective maintenance of non-conformities that may put an asset at risk, thereby ensuring safety, quality, and risk management or maintenance.

<h4>Technologies Used in the Project</h4>

<h5>Backend:</h5>

- Java and Spring Boot:
  <br><br>
  	- The REST APIs for the application's CRUD operations were built using Spring Boot;
  
	- Login security and report generation were implemented through Spring Security;
  <br><br>
  
- Oracle Cloud (AWS): 
  <br><br>
    A cloud database was adopted to support the application data with a connection via Oracle Wallet;
  <br><br>
  
- Maven: 
  <br>  
    Used to version and manage libraries, facilitating all developers and users to utilize the most up-to-date code, especially for maintaining the Java libraries used, which aids in the process and installation of the final code;
  <br><br>

<h5>Frontend:</h5>

- Vue.js: 
  <br>
    The entire visual design of the web page was created using this technology, including reports and the creation of inspection documents;
  <br><br>
  
- TypeScript:
  <br>
    Logic for the pages, including restrictions, data filling, and filtering of data selected by users, connecting and utilizing the APIs created in Java/Spring Boot;
  <br>

<h4>Individual Contributions</h4>

<details>
<summary>Backend</summary>
  <details>
<summary>REST API</summary>
  
- Using Spring Boot, I created the APIs to be consumed, both for creating reports and for selecting values of clients and their already registered reports.

Example:

<pre><code>
@RestController
@RequestMapping(value = "/sector")
public class SectorController {
    @Autowired
    private ISectorService service;

    @GetMapping
    public List<Sector> getAllSectors() {
        return service.getAllSectors();
    }

    @PostMapping
    public Sector createSector(@RequestBody Sector sector) {
        return service.createSector(sector);
    }

    @GetMapping(value = "/{sector}")
    public Sector getById(@PathVariable("sector") Long id) {
        return service.getById(id);
    }
}
</code></pre>

In this example, I used GET and POST methods to receive data from the frontend. Since the frontend sends data in JSON format, Vue.js sends its objects and attributes according to the database, as defined in the backend entities. For the method `GET /sector/{sector}`, an object of type Sector is received by the API, utilizing the ID parameter for the search present in the service used (to find the record with the specific ID). The `POST /sector` method is used to receive the Sector object with the parameters entered in the frontend, aiming to create a new sector record. The `GET /sector` method selects all sector records.
  </details>
</details>

<details>
<summary>Frontend</summary>
  <details>
	<summary>REST API Requests</summary>
	
Example of a REST request that consumes the Spring Boot backend API:

<pre><code>
// Function to fetch sectors from the database
async function fetchSector() {
    try {
        const response = await axios.get('sector');
        SelectionSection.value = response.data;
    } catch (error) {
        console.error('Error fetching service:', error);
    }  
}
</code></pre>

In this function, I am consuming the route `'/sector'` which returns an object with the list of registered sectors.
  </details>

<details> 
		<summary>Vue.js</summary>
		
Example of using the request in Vue.js:
```
<label>Setor: </label>
<select class="setor" id="setor" v-model="setor" @change="getSetor()">
    <option v-for="s in setores" :key="s.id" v-bind:value="s.id">{{ s.nome }}</option>
</select>
```
Using the Vue.js framework, it was possible to store the list of sectors to be displayed in the project view using `v-model`. In the example above, the sectors appear for selection within an HTML select. By selecting via the `@change` annotation, the ID of the relevant sector is saved to update the record in the database.
	</details>
</details>

<h4>Effective Learning:</h4>

<summary>REST Requests:</summary>
- Understanding how to consume and utilize a REST API through sending an appropriate request body and handling the responses was one of the key learnings.
<br><br>
<summary>Vue.js:</summary>
- The framework enabled the use of routers, allowing for multiple user interfaces within the same view.
- The ability to use constants directly in HTML through v-model.
<br><br>
<summary>Database Connection via AWS Wallet:</summary>
- We utilized an AWS wallet in the repository, enabling database connection without extensive configurations in the application properties on any machine that had it.
<br><br>
<summary>Spring Security:</summary>
- By using Spring Security, it was possible to implement user-level validations in the application by adding encrypted hash passwords and separating users by access level.
<br><br>
<summary>Spring and JPA:</summary>
- The save() function works for both Insert and Update; that is, an object that does not exist will have no ID and thus represents a new record. Conversely, an object with an existing ID will overwrite the registered values in the database with the attributes it contains, using the ID for the update (where the update is the ID of the object in question). This is automatically handled in the Spring save() function.

## Conclusion

The project developed in partnership with JAIA resulted in an effective system for managing building inspections and maintenance. Using technologies such as Java, Spring Boot, and Vue.js, we created a robust API and an intuitive interface that meets the client's needs.

The implemented features ensure simple navigation and agile data manipulation, promoting security and efficiency in property management. Thus, the system not only meets the requirements but also establishes a solid foundation for future improvements.

<!-- Navigation Links -->
<a href="#top">Back to top</a>

<br>

<div id="portfolio5Tecsus">
	<h1>API Project with Academic Partner TecSUS (2024-1)</h1>
</div>

[Link to Project Repository](https://github.com/quarks-team/Projeto-Integrador-TecSUS)

## Objective

The main objective of this project was to develop a **Web Dashboard** of high complexity, capable of processing and analyzing energy and water bills from various customer units. The system allows companies to identify opportunities for cost reduction and optimization of contracts with suppliers. Additionally, the dashboard offers functionalities for generating detailed reports and alerts based on consumption, providing a clear view of the performance and costs of each unit or contract.

## Technologies Used

- **Node.js**: 
  - Utilized for building a scalable backend API, Node.js allows for handling multiple requests simultaneously, making it ideal for real-time data processing and interaction with the frontend.
  
- **MySQL**: 
  - A relational database management system chosen for its robustness and efficiency in storing and querying structured data, ensuring data integrity and facilitating complex queries.
  
- **Vue.js**: 
  - Employed as the frontend framework to create a dynamic and responsive user interface. Vue.js offers a component-based architecture that enhances code reusability and simplifies the development process.
  
- **Docker/Docker Compose**: 
  - Used for containerizing the application, ensuring a consistent development and production environment. Docker simplifies dependency management and application deployment, allowing for seamless integration and scalability.

- **Power BI**: 
  - Integrated for data visualization and reporting. Power BI enables the creation of interactive dashboards that help stakeholders make informed decisions based on real-time data insights.

- **TypeScript**: 
  - Adopted to enhance JavaScript with static typing, improving code quality and maintainability. TypeScript allows for better tooling and error detection during development, contributing to a more robust application.


## My Contributions

### Dimensional Modeling
- I participated in dimensional modeling, creating a database that facilitated the analysis of large volumes of data. This architecture allowed for the generation of quick and efficient reports, essential for handling multiple bills per unit, contract, and supplier without compromising performance.
- I was involved in all phases of modeling: initial conception, construction, and implementation of fact and dimension tables. I worked on defining how the tables would relate to each other, considering the specificities of energy and water data. I also developed the queries for loading data into the fact tables, ensuring integrity and efficiency during the ETL process.

<details>
<summary>Dimensional Modeling</summary>
<img src="https://github.com/quarks-team/Projeto-Integrador-TecSUS-Database/blob/main/modelagem_banco_API_v.06.png">
</details>

### Backend with Node.js
In this example, I developed a **controller** in Node.js that allowed the user to upload their files through the frontend and track the progress of the upload and the ETL process. Since file uploads could take up to 5 minutes, it was essential to keep the user informed about the remaining time for the completion of the load.

<details>
<summary>Example of Controller in Node.js</summary>
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
            message: \`The file "\${file.originalname}" was processed successfully.\`,
          })}\n\n`,
        );
      }
    });
    await Promise.all(filePromises);
    if (global.sseResponse) {
      global.sseResponse.write(
        `event: user-log\ndata: ${JSON.stringify({
          message: 'All files were processed successfully.',
        })}\n\n`,
      );
      global.sseResponse.end();
    }
    return { message: 'All files were processed successfully.' };
  }
}
</code></pre>
</details>

### ETL with Node.js
I implemented the **ETL** (Extract, Transform, Load) logic to insert data into the tables, checking which files the user uploaded and processing them accordingly. The system verified whether the loaded data belonged to contracts or bills for water or energy, and only performed the load into the respective fact tables, ensuring data integrity and consistency.

<details>
<summary>Example of Data Transformation and Load</summary>
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
    // Process data, check for duplicates, and insert into time and bill tables
    // Loading into the fact tables occurs only after necessary checks
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

  // Helper function to remove duplicates from an array
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

### Verification and Loading into Fact Tables
After the transformations, the loading process into the water or energy fact tables was executed. The load only occurred if there were relevant new data, ensuring efficiency and avoiding duplicates.

<details>
<summary>Loading into Fact Tables</summary>
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

### Branch Strategy and Requirement Traceability
The **Trunk-Based Development** strategy was implemented to ensure that the entire team worked from the most up-to-date version of the code. This way, all new features and bug fixes were developed from a branch cloned from the main, allowing for smoother collaboration among team members.

This approach not only ensured that all developers were aligned with the latest version of the code but also facilitated the identification of the requirements being addressed in each task. Each branch created included the task ID, allowing it to be directly linked to the corresponding User Story, which described which requirements would be met. This way, the team was able to track the progress and implementation of requirements clearly and organized, ensuring an efficient workflow and delivery of solutions aligned with the project needs.

## Effective Learning

During the development of this project, I learned a lot about various fundamental areas of building complex systems, such as:

### Dimensional Modeling
- I worked intensively with dimensional modeling, which is essential for handling large volumes of data and ensuring agile reporting.

### Node.js
- The use of Node.js in scalable backends was advantageous for both performance and ease of integration with data processing libraries.

### SQL and Optimized Queries
- Optimizing queries for large databases, especially those related to calculating metrics and aggregations, was crucial for maintaining the system's efficiency.

### DevOps
- I learned about the principles and practices of DevOps, which emphasize collaboration between development and operations teams to automate and improve the software development lifecycle. Implementing a DevOps pipeline allowed for the integration of automated testing, continuous integration, and continuous delivery (CI/CD), ensuring that updates and deployments were faster, safer, and more reliable. This not only improved code quality but also increased overall development process efficiency.

### Conclusion

This project was a great opportunity to expand my skills as a developer, especially while working with new technologies for me, such as Node.js and dimensional modeling. Using Node.js in the backend allowed me to create efficient and scalable APIs, providing valuable learning in a stack that I did not yet dominate. Additionally, dimensional modeling enhanced my ability to organize and structure data for more powerful analyses, optimizing the performance of visualizations in Power BI.

Implementing a DevOps pipeline ensured a continuous and traceable development cycle, allowing for an agile and reliable process. In the end, the developed system offers important insights for the client, improving contract management and strategic decision-making. The project transformed me into a more complete developer, integrating backend, ETL, and data visualization skills into a single efficient and well-structured ecosystem.

<!-- Navigation Links -->
<a href="#top">Back to top</a>

<br>

<div id="portfolio6SpcGrafeno">
	<h1>In 2024-2, an API project was developed with the academic partner SPC Grafeno</h1>
	* [Link to Project Repository](https://github.com/quarks-team/Projeto-Integrador-SPCGrafeno)
	<h2> LOADING .... </h2>
</div>

