# Forecast_fuel
Com a variação excessiva dos preços dos combustíveis, e a surpresa sempre que ia ao posto, decidi fazer um previsor de preço de combustível, para poder me programar para o próximo abastecimento e não tomar um susto e prejuízo na carteira.

 ## *Sumario*
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
Gostaria de deixa claro que fiz os teste de correlação, todos no estado de Sao Paulo.

![image](https://user-images.githubusercontent.com/78280594/120376095-d74d3400-c2f1-11eb-8a76-e9eefbbb90b1.png)



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
