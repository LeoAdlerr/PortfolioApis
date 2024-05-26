<h3> Em 2021-2 foi trabalhado um projeto API com cliente interno(professores da Fatec) </h3> 
* [Video Apresentação do projeto](https://www.youtube.com/watch?v=0aUKWEjipQQ)
 
* [Link para o GitHub](https://github.com/LeoAdlerr/Projeto-Integrador-2021-2-Grupo3/tree/main)

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


  

  
