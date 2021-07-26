# Projeto de análise e previsão do índice de novos casos de Covid-19 no RJ.

<p align="center"><img src=https://veja.abril.com.br/wp-content/uploads/2020/07/PRAIA-DO-LEME-RIO-DE-JANEIRO-COVID-19-BRASIL-2020-12.JPG.jpg?quality=70&strip=info&resize=680,453 </p> 

# **Introdução**

Este é o terceiro projeto feito por mim em função do Bootcamp de Data Science aplicada da Alura. Nele usarei os processos de análise e manipulação de dataframes em conjunto com ferramentas gráficas para analisar séries temporais, inicialmente comparando a evolução no número de casos no estado do Rio de Janeiro com a evolução no número de Casos na cidade de Berlim, Alemanha. Em seguida, utilizarei-me de métodos estatíticos e da biblioteca Prophet para formular um modelo preditivo dos novos casos de Covid-19 no estado do Rio de Janeiro.

## **Comparação entre Rio de Janeiro e Berlim**

Sendo um típico brasileirinho que sou fiquei e fico indignado com a postura adotada pelas autoridades em relação ao combate à Covid-19 no país: Demora para tomar as primeiras iniciativas preventivas, posicionamento anti-científico, etc. Assim, me veio a ideia de comparar o meu querido estado, Rio de Janeiro, um estado que mesmo enfrentando uma das maiores médias de óbitos a cada 100 mil habitantes na época [[1]](https://brasil.elpais.com/brasil/2021-03-07/rio-de-janeiro-adota-lockdown-envergonhado-enquanto-infeccoes-pela-covid-19-aceleram.html) demorou a tomar medidas como o lockdown, com outro grande centro urbano que aplicou com eficácia a prática de lockdown e testar a hipótese de que essa medida realmente poupa vidas. Essa ideia ficou ainda mais interessante pois a Alemanha passou de exemplo ao combate da doença, durante a primeira onda de Covid-19, para um exemplo de como a falsa sensação de segurança e o relaxamento das medidas podem condenar parte da população e fazer subirem drasticamente os índices de casos e mortes[[2]](https://brasil.elpais.com/sociedad/2020-12-17/como-a-alemanha-passou-de-exemplo-na-pandemia-a-um-dos-paises-mais-golpeados-pela-covid-19-na-europa.html).

O dataframe que obtive com os dados de Berlim contava com um índice específico: novos casos a cada 100 mil habitantes nas duas últimas semanas, calculados semanalmente, então manipulei o dataframe que possuia para o estado do Rio de Janeiro a fim de gerar esse índice e poder comparar ambos os Estados. Assim, pude comparar os índices de novos casos a cada 100 mil habitantes de ambos os estados e testar a hipótese de que as medidas de afastamento social são eficazes e necessárias no combate de uma doença de fácil transimssão como é a Covid-19. Finalmente, pude também comparar o índice anteriormente citado no momento em que Berlim passava por uma crise durante a segunda onda com os do Rio de Janeiro.

# **Dados**

Os dados utilizados neste projeto foram obtidos do [Brasil.io](https://brasil.io/dataset/covid19/caso_full/), que disponibiliza dados sobre os casos e óbitos relacionados à Covid-19 no Brasil, e também do [ European Centre for Disease Prevention and Control ](https://www.ecdc.europa.eu/en/covid-19/data), que fornece dados quanto ao combate da Covid-19 em diversos países dentro da União Européia.
Eu escolhi os dataset: 
- caso_full, que possui os dados para todos os municípios do país.
- Data on the weekly subnational 14-day notification rate of new COVID-19 cases[[3]](https://www.ecdc.europa.eu/en/publications-data/weekly-subnational-14-day-notification-rate-covid-19), que possui o índice de novos casos a cada 100 mil habitantes das últimas 2 semanas, feito semanalmente, de uma grande gama de estados de diversas nações dentro da União Européia.

Os dados Europeus estaram na pasta Dados no [GitHub do projeto](https://github.com/lucasfranca016/Projeto_previsao_covid_RJ), contudo, por ser maior terei que apenas disponibilizar o link para baixar o outro [conjunto de dados referentes aos estados brasileiros](https://brasil.io/dataset/covid19/caso_full/).

# **Hipóteses**

- A prática de medidas de afastameto social bem aplicadas reduzem a propagação do Covid-19.

- O número de casos no Rio de Janeiro deve diminuir por conta do início da campanha de vacinação.

# **Estrutura do notebook:**

- Importação das bibliotecas usadas.

- Importação dos dados.

- Tratamento dos dados para comparação entre RJ e Berlim.

- Primeira análise dos dados.

- Tratamento dos dados para uso do Prophet.

- Construção de um modelo preditivo.

 - Previsão de novos casos no RJ.
 
- Comentários sobre o modelo.
 
- Conclusões.

- Projeções futuras.

## **Comentários sobre o modelo**

O primeiro modelo foi criado utilizando o parâmetro change_prior_scale, que muda o quanto o modelo se molda às curvas dos dados, igual à 5 pois é um valor um pouco mais alto que o valor padrão, que é 0.5, assim, gera um fit melhor aos dados, mas evitamos um valor ainda maior para não ocorrer um overfit. Quando tratamos de séries temporais com sazonalidades e padrões o parâmetro de sazonalidade multiplicativa se encaixa melhor. Fora isso, só foram adicionados os feriados. 

Como nossa base de dados é de notificações de casos novos observamos muitas irregularidades e padrões, que até mesmo o Prophet identifica e nos mostra, logo, percebemos que existem pontos muito fora do padrão.Tendo isso em vista, é feito um recorte de outlier para criarmos um modelo mais preciso e os outliers foram selecionados como aqueles valores que se encontravam fora do intervalo de confiança, ou incerteza, alcançada pelo primeiro modelo.

Assim, comparados as quantidades como o R² e o erro absoluto da média, que são quantidades que comparavam o valor previsto com o valor real, vemos que o modelo com outliers removidos gera melhores resultados e então seguimos com ele.

## **Conclusões**

- Observamos a partir do primeiro gráfico, o gráfico que compara o índice de novos casos a cada 100 mil habitantes entre as cidades de Berlim e Rio de Janeiro, que durante a primeira onda o Rio de Janeiro sofre com um grande número de novos casos  e que só para de decrescer em meados de Agosto, enquanto que em Berlim no mesmo período esse índice se encontra estável e com um número de casos bastante inferior, assim, fortalecendo a hipótese de que medidas de isolamento social são eficazes no combate à Covid-19 se bem aplicadas.Aliado à análise gráfico temos o teste de hipótese aplicado que corrobora nossa tese.


- Observamos um claro aumento no número de casos em ambos os estados aproximadamente no mês de Outubro de 2020 e Março de 2021, representando as segunda e terceira onda. O Rio de Janeiro, que não conseguiu estabilizar o número de novos casos, sofre com o contínuo aumento desse índice em média, apesar de alguns momentos de descréscimo, já Berlin que relaxou suas medidas sofreu o impacto dessa segunda onda intenssamente, contudo, propôs novas medidas de isolamento social para parar o aumento de novos casos e controlar a crise no estado.

- Para relacionar a diminuição ou o estabilização no índice de novos casos de Covid-19 com a prática de Lockdown ou outras medidas de distanciamento social precisamos analisar também a influência de outras possíveis variáveis nesse índice, tais como o investimento em saúde pública por exemplo. Uma análise muito mais minuciosa e elaborada é feita no artigo [[4]](https://www.nature.com/articles/s41586-020-2404-8.pdf).

- O modelo feito neste trabalho gera previsões razoáveis para até 30 dias além dos dados, contudo, suas taxas de incerteza e erro relacionados as previsões aumentam muito após a faixa de 30 dias de previsão. Assim, à primeira vista poderiamos dizer que é razoável pensar que o índice de novos casos irá crescer no próximo mês, contudo, essa previsão deve ser levada com várias ressalvas devido aos motivos já previamente mencionados e também pelo fator dele não englobar variáveis que podem influenciar esse índice como a própria campanha de vacinação atualmente em curso. Logo, é justo falarmos que a hipótese de que os casos vão diminuir ou até mesmo estabilizar no mês de Julho não é corroborada pelo modelo.

## **Projeções futuras**

- Para analisar melhor a hipótese de que medidas de distanciamento social são eficazes na contenção da Covid-19 podemos fazer uma análise mais parecida com a do artigo previamente mencionado e analisar diversos países que adotaram medidas de proporções diferentes e estudar como evolui o índice de novos casos e óbitos nos mesmos.

- Um melhor estudo sob a biblioteca Prophet se faz necessária para a melhor parametrização do modelo para que assim possamos gerar melhores previsões à cerca da evolução de casos no estado do RJ. 

- Uma outra forma de análise a ser testa pode ser a de separar os dados em amostras de teste e de treino de forma randômica para que assim não precisemos usar os dados do Mês de Junho para teste, logo os englobando e fazendo com que a previsão de 30 dias no futuro englobe todo o mês de Julho, então diminuindo as incertezas e erros relacionados às previsões dos dias que não possuimos dados ainda.

## **Referências**

[[1]](https://brasil.elpais.com/brasil/2021-03-07/rio-de-janeiro-adota-lockdown-envergonhado-enquanto-infeccoes-pela-covid-19-aceleram.html) "Rio de Janeiro adota lockdown envergonhado enquanto infecções pela Covid-19 aceleram".

[[2]](https://brasil.elpais.com/sociedad/2020-12-17/como-a-alemanha-passou-de-exemplo-na-pandemia-a-um-dos-paises-mais-golpeados-pela-covid-19-na-europa.html) "Como a Alemanha passou de exemplo na pandemia a um dos países mais golpeados pela Covid-19 na Europa.

[[3]](https://www.ecdc.europa.eu/en/publications-data/weekly-subnational-14-day-notification-rate-covid-19)"Weekly subnational 14 day notification rate Covid-19"

[[4]](https://www.nature.com/articles/s41586-020-2404-8.pdf)."The effect of large-scale anti-contagion policies on the COVID-19 pandemic"
