# Forecast_fuel
[![Generic badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/matheus-laet/)


Com a variação excessiva dos preços dos combustíveis, e a surpresa sempre que ia ao posto, decidi fazer um previsor de preço de combustível, para poder me programar para o próximo abastecimento e não tomar um susto e prejuízo na carteira.

 ## **Sumario**
- [Objetivo](https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/index.md#objetivo-do-projeto) 
- [Features](https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/index.md#Features)
- [EDA](https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/index.md#gr%C3%A1ficos-da-eda)
- [Colelações](https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/index.md#correla%C3%A7%C3%B5es-identificadas)
- [Modelos](https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/index.md#modelos)


## Objetivo do Projeto
como objetivo busco mostrar a previsao do preço do combustivel(gasolina, etanol e disel) medio por estado.

## Features

Neste projeto retiramos os dados históricos das bases de dados dos sites,  [Gov- Agência Nacional de Petróleo](https://www.gov.br/anp/pt-br/centrais-de-conteudo/dados-abertos), que foi retirado dos preços de compra e venda dos combustíveis e o [IndexMundi](https://www.indexmundi.com/),  onde foi retirado outras variaveis, como preço da bolsa, preço do petróleo bruto, etanol futuro e preço bruto do diesel. 

## Gráficos da EDA
analise BoxPlot dos valores de venda.
Podemos identificar poucos valores no estado do Amapa, provavelmente impossibilitando o treinamento adequado do nosso modelo.
![image](https://user-images.githubusercontent.com/78280594/120231975-f03de280-c228-11eb-92fd-4d23ceb6b9dc.png)

Durante a analise lembrei da Greve dos caminhoneiros que ocorreu em 2018, paralizando o serviços como fornecimento de combustíveis, distribuição de alimentos e insumos médicos, a greve teve como uma das principais exigencias a redução nos preços do Diesel e demais combustiveis durou da cerca de 10 dias, iniciando dia 21/05 e terminando dia 30/05.

* Aqui vemos a variação do preço de venda do combustivel no estado de Sao Paulo no mesmo periodo da greve.
![image](https://user-images.githubusercontent.com/78280594/120232779-a2c27500-c22a-11eb-8cf9-45a19144fae2.png)

* Variação do preço de compra dos combustiveis no mesmo periodo no mesmo estado.
![image](https://user-images.githubusercontent.com/78280594/120232916-f46aff80-c22a-11eb-8268-22898ad3305f.png)

## Correlações identificadas
:warning: Todos os testes de correlação foram feitos no estado de São Paulo. :warning:

A correlação é, a dependência que as variáveis têm entre si, quando as dependências não são obvias utilizamos os métodos de detecção como os índices de [Pearson](https://pt.wikipedia.org/wiki/Coeficiente_de_correla%C3%A7%C3%A3o_de_Pearson), [Spearman](https://pt.wikipedia.org/wiki/Coeficiente_de_correla%C3%A7%C3%A3o_de_postos_de_Spearman) e [Kendall](https://pt.wikipedia.org/wiki/Coeficiente_de_correla%C3%A7%C3%A3o_tau_de_Kendall#:~:text=Em%20estat%C3%ADstica%2C%20o%20coeficiente%20de,postos%20entre%20duas%20quantidades%20medidas.).

correlação das variaveis da Gasolina | correlação das variaveis do Etanol | correlação das variaveis do Diesel
:-------------------------:|:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/78280594/120418821-a09a0c80-c337-11eb-8df3-07b8e9f9a027.png)  |  ![image](https://user-images.githubusercontent.com/78280594/120418855-ae4f9200-c337-11eb-9212-69fae0965661.png) |  ![image](https://user-images.githubusercontent.com/78280594/120418917-c6271600-c337-11eb-824f-a8750e9b5e88.png)




Para diminuir os riscos de Overfiting e ser mais logico a forma de trabalhar com os valores, fiz um deslocamento de data das variáveis, fazendo o teste com deslocamento de 1 e 2 meses para testar a correlação.


<img src="https://raw.githubusercontent.com/matheus-laet/Forecasting_fuel/gh-pages/imagens/output_LpsubZ.gif" alt="Gif" width="400"/>



Correlação lag de 1 mês    |  Correlação lag de 2 mês          
:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/78280594/120415331-be647300-c331-11eb-9c84-2fc83544e721.png)  |  ![image](https://user-images.githubusercontent.com/78280594/120415377-d0deac80-c331-11eb-9808-3f9b15745e10.png)



## Modelos
### _- Arima_
O ARIMA (AutoRegressive Integrated Moving Average), utiliza dados passados para prever o futuro, usando dois principais recursos: a autocorrelação e médias móveis.


### _- XGBoost_
O XGBoost é um algoritimo baseado em Gradient boosting que constrói o modelo em etapas, e os generaliza.


### _- Prophet_
O Prophet é um pacote usado pelo Facebook, que implementa algoritimos de previsões de series temporais, feito para detectar automaticamente os padroes sazonais de uma serie.


### _- CatBoost_


## Resultados Comparativos


## Board de visualizações finais

