# Análise de crimes na cidade de Vancouver



## Contextualização

Vancouver é uma importante cidade no oeste do Canadá, está localizada na província de British Columbia. Segundo o censo de 2016, a cidade tem um total de 631 436 habitantes, fazendo dela a cidade mais populosa da província. É comum observar que em grandes centros urbanos a taxa de criminalidade é maior do que em médias e pequenas cidades. Todavia, a pergunta é: **Vancouver é uma cidade perigosa?** 

## Plano de análise de dados
#### Objetivos

Neste projeto, foi realizado uma análise de dados referentes ao crimes ocorridos nesta cidade durante o período do ano de 2003 até 2016 com o objetivo de elucidar algumas questões:
1. Os crimes são mais frequentes em qual período do dia?
2. Os crimes aumentaram ou diminuíram com o passar dos anos?
3. Quais crimes foram mais frequentes em cada ano?
4. Qual é a quantidade de crime total por período do ano?
5. Qual região/bairro de Vancouver com maior número de roubo de algum pertence do veículo?

#### Fonte de dados

O *dataset* utilizado nesse projeto está disponível para download em https://www.kaggle.com/wosaku/crime-in-vancouver. O arquivo original contém dados de 2013 a 2017, mas aqui foram analisados apenas até o período de 2016, pois não há infomação completa do ano de 2017.

A tabela possui 12 colunas:
- **Type:** descreve o tipo de crime;
- **Year, Month, Day, Hour, Minute:** informações temporais de quando ocorreu o crime;
- **Hundred_Block, Neighbourhood:** informações espaciais;
- **X, Y, Latitude e Longitude:** Coordenadas UTM e geográficas.


#### Ferramenta utilizada

A análise de dados foi realizada em linguagem SQL (MySQL). Optei por usar essa ferramenta porque eu queria realizar uma análise completa nessa linguagem a fim de disponibilizar no meu portfolio de projetos. Todavia, com os resultados obtidos da análise, eu criei um Dashboard usando Python e Dash para complementar a apresentação dos meus resultados. Convido a acessá-lo em: https://crimes-vancouver.herokuapp.com. 


#### Aplicação das técnicas de análise

Foi realizadado a análise exploratória do dado e foi verificado quem o banco de dados não possui nenhuma informação espacial do local do crime quando este se trata de crime contra a pessoa, acredito que seja por conta de privacidade. Sendo assim, eu optei por realizar queries que desconsiderassem tais dados do dataset. Todos registros que contribuíram para esse relatório possuem as informações de todos os campus.  Como já foi dito, os dados referentes ao ano de 2017 estão incompletos, por isso eles não foram incluídos nessa análise. Técnicas de agregação, funções ao longo tempo, queries/subqueries e views materializadas foram desenvolvidas ao longo do processo. 

#### Entrega dos resultados

A entrega dos resultados ocorrerá através de um relatório com as principais conclusões da análise e tabelas, sugestões e um dashboard disponibilizado na web que responda e elucida as questões iniciais ou até outras mais. O relatório está no próximo ítem.


## Relatório

### 1) Os crimes são mais frequentes em qual período do dia?

A partir das informações da hora em que ocorreu o crime, o período de 0 hora até 11 horas foi classificado como **AM** e de 12 às 23 horas como **PM**. Agrupando todos crimes apenas por turno, independentemente do tipo de crime, bairro etc, os crimes são mais frequentes no turno PM com 306379 crimes enquanto que no outro turno teve um total de 151444.

| Part of day | Amount  | Percentage |
| ----------- | ------- | ---------  |
|     PM      | 3066379 |   66.92%   |
|     AM      | 151444  |   33.07%   |


### 2) Os crimes aumentaram ou diminuíram com o passar dos anos?

O gráfico abaixo mostra duas informações ao longo tempo: a quantidade absoluta de crimes que ocorreram em cada ano e uma média móvel ao longo de cada ano.

![image](https://user-images.githubusercontent.com/45640708/158600160-0537d32d-df13-4053-98e0-be12950996f0.png)

Observamos que os crimes dimiuíram até a atingir a quantidade mínima no ano de 2011 e depois voltou a crescer. 

### 3) Quais crimes foram mais frequentes em cada ano?

A tabela abaixo mostra os dois tipos de crimes com maior frequência em cada ano.

|        Type | Year    |  Amount    |
| ----------- | ------- | ---------  |
|  Theft from Vehicle     | 2003   |  17287   |
| Break and Enter Residential/Other    | 2003    | 6883 | 
 | Theft from Vehicle    | 2004    | 17835 | 
 | Break and Enter Residential/Other    | 2004    | 6537 | 
 | Theft from Vehicle    | 2005    | 16265 | 
 | Break and Enter Residential/Other    | 2005    | 5542 | 
 | Theft from Vehicle    | 2006    | 14580 | 
 | Break and Enter Residential/Other    | 2006    | 5674 | 
 | Theft from Vehicle    | 2007    | 12152 | 
 | Break and Enter Residential/Other    | 2007    | 4996 | 
 | Theft from Vehicle    | 2008    | 11231 | 
 | Mischief    | 2008    | 5261 | 
 | Theft from Vehicle    | 2009    | 9956 | 
 | Mischief    | 2009    | 4421 | 
 | Theft from Vehicle    | 2010    | 8567 | 
 | Mischief    | 2010    | 4486 | 
 | Theft from Vehicle    | 2011    | 7404 | 
 | Mischief    | 2011    | 4812 | 
 | Theft from Vehicle    | 2012    | 8065 | 
 | Mischief    | 2012    | 4235 | 
 | Theft from Vehicle    | 2013    | 8298 | 
 | Mischief    | 2013    | 4173 | 
 | Theft from Vehicle    | 2014    | 10097 | 
 | Mischief    | 2014    | 4509 | 
 | Theft from Vehicle    | 2015    | 10480 | 
 | Other Theft    | 2015    | 4678 | 
 | Theft from Vehicle    | 2016    | 12735 | 
 | Other Theft    | 2016    | 5708 | 


Para saber a distribuição de um crime específico para um determinado ano por bairro, você pode usar o Dashboard e aplicar os filtros adequados.

### 4) Qual é a quantidade de crime total por período do ano?

A partir das informações do dia e mês do ano, os dados foram organizados por estação do ano a fim de verificar se existia um padrão. 


|   Season |   Amount    |
| ----------- |  ---------  |
  | Summer  | 122205  | 
  | Spring  | 115924  | 
  | Autumn  | 110739  | 
  | Winter  | 108955  | 
  
  Como podemos ver na imagem abaixo - distribuição dos crimes ao longo dos anos por estação - os crimes ocorrem mais no verão e primavera.
  
  ![image](https://user-images.githubusercontent.com/45640708/158611950-0a2ba34a-bb87-4824-8e17-dce5ff55357a.png)

  
 ### 5) Qual região/bairro de Vancouver com maior número de roubo de algum pertence do veículo?

Na imagem abaixo temos a distribuição desse crime por bairro ocorrido no período total da análise.

![image](https://user-images.githubusercontent.com/45640708/158615534-ad151792-4cfe-4f4c-a0dd-f402e7ffcb6f.png)

Na imagem abaixo temos a distribuição desse crime ocorrido ao longo dos anos.

![image](https://user-images.githubusercontent.com/45640708/158615780-7e7e86ee-a631-4cbf-8204-8871bc705deb.png)


## Conclusões e sugestões

Verificamos que os crimes ocorrem mais frequência na segunda parte do dia e as maiores taxas ocorrem no período do verão e primavera. Acredito que a ocorrência nestas estações do ano esteja associada em virtude da maior exposição da população fora de casa, tendo em vista que as pessoas tendem a estar mais fora de casa por conta temperatura. 

A quantidade total de crimes tem uma relação muito forte com o crime "Theft from vehicle", uma vez as autoridades prevenindo e combatendo esse tipo de crime, a taxa de criminalidade da cidade certamente diminuirá consideravelmente. O local de Vancouver com mais incidência para esse tipo de crime é a região cetral da cidade, o que é completamente explicada pela densidade demográfica. 

Tomando como ponto de partida os padrões observados nesse conjunto de dados, seguem algumas sugestões:
1. Distribuição desigual do efetivo da polícia- mais polícia onde temos mais crimes;
2. As escalas, folgas e férias dos policiais devem ser pensadas de acordo com incidência de crimes. Por exemplo, o melhor período do ano para os policiais tirarem férias é no período do inverno. Verão e primavera devem ter o efetivo máximo;
3. Política de conscientização da população em relação a deixar pertences dentro do veículo.


