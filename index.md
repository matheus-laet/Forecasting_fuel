[![Generic badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/matheus-laet/)
[![Generic badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/matheus-laet)

# Forecast_fuel

Com a variação excessiva dos preços dos combustíveis e a surpresa sempre que ia ao posto, decidi fazer um previsor de preço de combustível, para poder me programar na próxima vez que for abastecer e não tomar um susto e prejuízo na carteira.

 <H2> Sumario </H2>
 
- [Objetivo](#objetivo-do-projeto)

- [Features](#features)

- [EDA](#gr%C3%A1ficos-da-eda)

- [Colelações](#correla%C3%A7%C3%B5es-identificadas)

- [Modelos](#modelos)
 

## Objetivo do Projeto
como objetivo busco mostrar a previsao do preço do combustivel(gasolina, etanol e disel) medio por estado.

## Features

Neste projeto retiramos os dados históricos das bases de dados dos sites,  [Gov- Agência Nacional de Petróleo](https://www.gov.br/anp/pt-br/centrais-de-conteudo/dados-abertos), que foi retirado dos preços de compra e venda dos combustíveis e o [IndexMundi](https://www.indexmundi.com/),  onde foi retirado outras variaveis, como preço da bolsa, etanol futuro e preço bruto do diesel. 

## Gráficos da EDA
analise BoxPlot dos valores de venda.
Podemos identificar poucos valores no estado do Amapa, provavelmente impossibilitando o treinamento adequado do nosso modelo.
![image](https://user-images.githubusercontent.com/78280594/120231975-f03de280-c228-11eb-92fd-4d23ceb6b9dc.png)

Durante a análise, lembrai da Greve dos caminhoneiros que ocorreu em 2018, paralisando os serviços como fornecimento de combustíveis, distribuição de alimentos e insumos médicos, a greve teve como uma das principais exigências a redução nos preços do Diesel e demais combustíveis durou da cerca de 10 dias, iniciando dia 21/05 e terminando dia 30/05.

* Aqui vemos a variação do preço de venda do combustivel no estado de Sao Paulo no mesmo periodo da greve.
![image](https://user-images.githubusercontent.com/78280594/120232779-a2c27500-c22a-11eb-8cf9-45a19144fae2.png)

* Variação do preço de compra dos combustiveis no mesmo periodo no mesmo estado.
![image](https://user-images.githubusercontent.com/78280594/120232916-f46aff80-c22a-11eb-8268-22898ad3305f.png)

## Correlações identificadas
:warning: Todos os testes de correlação foram feitos no estado de São Paulo. :warning:

A correlação é, a dependência que as variáveis têm entre si, quando as dependências não são obvias utilizamos os métodos de detecção como os índices de [Pearson](https://pt.wikipedia.org/wiki/Coeficiente_de_correla%C3%A7%C3%A3o_de_Pearson), [Spearman](https://pt.wikipedia.org/wiki/Coeficiente_de_correla%C3%A7%C3%A3o_de_postos_de_Spearman) e [Kendall](https://pt.wikipedia.org/wiki/Coeficiente_de_correla%C3%A7%C3%A3o_tau_de_Kendall#:~:text=Em%20estat%C3%ADstica%2C%20o%20coeficiente%20de,postos%20entre%20duas%20quantidades%20medidas.).

correlação das variaveis da Gasolina | correlação das variaveis do  Etanol | correlação das variaveis do   Diesel
:-------------------------:|:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/78280594/120418821-a09a0c80-c337-11eb-8df3-07b8e9f9a027.png)  |  ![image](https://user-images.githubusercontent.com/78280594/120418855-ae4f9200-c337-11eb-9212-69fae0965661.png) |  ![image](https://user-images.githubusercontent.com/78280594/120418917-c6271600-c337-11eb-824f-a8750e9b5e88.png)




Para diminuir os riscos de Overfiting e ser mais logico a forma de trabalhar com os valores, fiz um deslocamento de data das variáveis, fazendo o teste com deslocamento de 1 e 2 meses para testar a correlação.


<img src="https://raw.githubusercontent.com/matheus-laet/Forecasting_fuel/gh-pages/imagens/output_LpsubZ.gif" alt="Gif" width="400"/>



Correlação lag de 1 mês    |  Correlação lag de 2 mês          
:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/78280594/120415331-be647300-c331-11eb-9c84-2fc83544e721.png)  |  ![image](https://user-images.githubusercontent.com/78280594/120415377-d0deac80-c331-11eb-9808-3f9b15745e10.png)



## Modelos
### metricas
Durante o desenvolvimento dos modelos, precisamos também fazer o cálculo das métricas, que são contas matemáticas para saber o desempenho dos nossos modelos.
Para esse projeto, escolhi o [Erro Abssoluto Medio](https://en.wikipedia.org/wiki/Mean_absolute_error), e o [Coeficiente de determinação(R2)](https://pt.wikipedia.org/wiki/Coeficiente_de_determina%C3%A7%C3%A3o).

 Para podermos entender melhor o resultado dos nossos modelos e a precisão, temos que analisar os residuos, que é o valor da diferença entre os resultados reais e os resultados previstos. Fazendo o histograma esperamos ver mais resultados em 0.
 
 
### _Arima_           
<img src="https://user-images.githubusercontent.com/78280594/120505080-0966a080-c39b-11eb-96f9-418d637a5cd7.png" alt="ARIMA" width="400"/>

O ARIMA (AutoRegressive Integrated Moving Average), utiliza dados passados para prever o futuro, usando dois principais recursos: a autocorrelação e médias móveis.

- _Resultados_

 Treino
<img src="https://user-images.githubusercontent.com/78280594/120535026-e1863580-c3b8-11eb-88c9-8a6dd904ebb4.png" alt="result" width="1200"/>
 Test
<img src="https://user-images.githubusercontent.com/78280594/120535071-ef3bbb00-c3b8-11eb-8fcd-7ff65f12c38a.png" alt="result" width="1200"/>


- _*Análises e Metricas*_ 


 _Metricas no Teste_     |  _Metricas no Treino_          
:-------------------------:|:-------------------------:
 Media do erro: 0.6125    |   Media do erro: 0.0203
 R2: -9.4277              |    R2: 0.9964
 

 <H4> Residuos </H4> 
 
<img src="https://user-images.githubusercontent.com/78280594/120546748-a25ee100-c3c6-11eb-9a0b-b46945e4a72e.png" alt="XGB" width="400"/>


### _XGBoost_         
<img src="https://user-images.githubusercontent.com/78280594/120505833-bc36fe80-c39b-11eb-8b51-1d80d8bfe3ae.png" alt="XGB" width="400"/>


O XGBoost é um algoritimo baseado em Gradient boosting que constrói o modelo em etapas, e os generaliza.


- _Resultados_

 Treino
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/comparacao_grafico_resultados_trainox.png?raw=true" width="1200"/>
 Test
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/comparacao_grafico_resultadosx.png?raw=true" width="1200"/>



- _*Análises e Metricas*_ 


_Metricas no Teste_     |  _Metricas no Treino_          
:-------------------------:|:-------------------------:
 Media do erro: 0.324178    |   Media do erro: 0.034639
 R2: -3.668369            |    R2: 0.984718
 

 <H4> Residuos </H4>
 
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/hist_residuosx.png?raw=true" alt="XGB" width="400"/>



### _Prophet_
<img src="https://user-images.githubusercontent.com/78280594/120506219-189a1e00-c39c-11eb-9d81-7ef350fc5783.png" alt="Prophet" width="400"/>

O Prophet é um pacote usado pelo Facebook, que implementa algoritimos de previsões de series temporais, feito para detectar automaticamente os padroes sazonais de uma serie.


- _Resultados_

 Treino
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/previsao_grafica_prophet_trainox.png?raw=true" width="1200"/>
 Test
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/previsao_grafica_prophetx.png?raw=true" width="1200"/>



- _*Análises e Metricas*_ 


_Metricas no Teste_     |  _Metricas no Treino_          
:-------------------------:|:-------------------------:
 Media do erro: 0.1543    |   Media do erro: 0.0442
 R2: 0.0274            |   R2: 0.978
 

<H4> Residuos </H4> 
 
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/hist_residuos_prophetx.png?raw=true" alt="XGB" width="400"/>





### _- CatBoost_
<img src="https://avatars.mds.yandex.net/get-yablogs/51163/file_1500371746775/orig" alt="XGB" width="400"/>

O CatBoost é um algoritimo baseado em Gradient boosting que constrói o modelo em etapas assim como o XGBoost, o diferencial dele é que ele trata as features categoricas sozinho.

- _Resultados_

 Treino
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/previsao_grafica_prophet_trainox.png?raw=true" width="1200"/>
 Test
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/previsao_grafica_prophetx.png?raw=true" width="1200"/>



- _*Análises e Metricas*_ 


_Metricas no Teste_     |  _Metricas no Treino_          
:-------------------------:|:-------------------------:
 Media do erro: 0.3338    |   Media do erro: 0.0971
 R2: -1.3391            |   R2: 0.0971
 

<H4> Residuos </H4> 
 
<img src="https://github.com/matheus-laet/Forecasting_fuel/blob/gh-pages/imagens/hist_residuos_prophetx.png?raw=true" alt="XGB" width="400"/>


## Resultados Comparativos


## Board de visualizações finais

