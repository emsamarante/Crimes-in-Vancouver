# Análise de crimes na cidade de Vancouver



## Contextualização

Vancouver é uma importante cidade no oeste do Canadá, está localizada na província de British Columbia. Segundo o censo de 2016, a cidade tem um total de 631 436 habitantes, fazendo dela a cidade mais populosa da província. É comum observar que em grandes centros urbanos a taxa de criminalidade é maior do que em médias e pequenas cidades. Todavia, a pergunta é: Vancouver é uma cidade perigosa? 

### Objetivos

Neste projeto, foi realizado uma análise de dados referentes ao crimes ocorridos nesta cidade durante o período do ano de 2003 até 2016 com o objetivo de elucidar algumas questões:
1. Os crimes são mais frequentes em qual período do dia?
2. Os crimes aumentaram ou diminuíram com o passar dos anos?
3. Qual crime foi mais frequente em cada ano?
4. Qual é a quantidade de crime total por período do ano?
5. Qual região/bairro de Vancouver com maior índice de roubo de veículo ou roubo de algum pertence do veículo?

## Fonte de dados

O *dataset* utilizado nesse projeto está disponível para download em https://www.kaggle.com/wosaku/crime-in-vancouver. O arquivo original contém dados de 2013 a 2017, mas aqui foram analisados apenas até o período de 2016, pois não há infomação completa do ano de 2017.

A tabela possui 12 colunas:
- **Type:** descreve o tipo de crime;
- **Year, Month, Day, Hour, Minute:** informações temporais de quando ocorreu o crime;
- **Hundred_Block, Neighbourhood:** informações espaciais;
- **X, Y, Latitude e Longitude:** Coordenadas UTM e geográficas.


## Ferramenta utilizada

A análise de dados foi realizada em linguagem SQL (MySQL). Optei por usar essa ferramenta porque eu queria realizar uma análise completa nessa linguagem a fim de disponibilizar no meu portfolio de projetos. Todavia, com os resultados obtidos da análise, eu criei um Dashboard usando Python e Dash para complementar a apresentação dos meus resultados. Convido a acessá-lo em: https://crimes-vancouver.herokuapp.com. 


## Aplicação das técnicas de análise

Foi realizadado a análise exploratória do dado e foi verificado quem o banco de dados não possui nenhuma informação espacial do local do crime quando este se trata de crime contra a pessoa, acredito que seja por conta de privacidade. Sendo assim, eu optei por realizar queries que desconsiderassem tais dados do dataset. Todos registros que contribuíram para esse relatório possuem as informações de todos os campus.  Como já foi dito, os dados referentes ao ano de 2017 estão incompletos, por isso eles não foram incluídos nessa análise. Técnicas de agregação, funções ao longo tempo, queries/subqueries e views materializadas foram desenvolvidas ao longo do processo.








