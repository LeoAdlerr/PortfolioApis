## Portfólio - Dashboard Web de Análise de Faturas de Energia, Água e Gás

### Objetivo
O principal objetivo deste projeto é desenvolver um **Dashboard Web** de alta complexidade, capaz de processar e analisar faturas de energia, água e gás de diversas unidades de clientes. O sistema permite que as empresas identifiquem oportunidades de redução de custos e otimização de contratos com concessionárias. O dashboard oferece funcionalidades de geração de relatórios detalhados e alertas baseados no consumo, possibilitando uma visão clara e direta sobre o desempenho e os custos de cada unidade ou contrato.

### Minhas Contribuições
(Contribuições futuras serão detalhadas nesta seção, relacionadas ao backend, frontend e integração de dados.)

### Aprendizado Efetivo

Durante o desenvolvimento deste projeto, obtive um aprendizado significativo em várias áreas fundamentais para a construção do sistema. Abaixo estão os principais tópicos de aprendizado:

#### Modelagem Dimensional
- Utilizei técnicas de **modelagem dimensional** para organizar o banco de dados, o que facilitou a análise de grandes volumes de dados, permitindo criar relatórios rápidos e eficientes. Isso foi crucial para que o sistema pudesse lidar com múltiplas faturas por unidade, contrato e concessionária, sem perder a performance.

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
