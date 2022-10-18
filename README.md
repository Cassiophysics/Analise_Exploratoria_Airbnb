
# Análise Exploratória de Dados - Airbnb RJ

![rj2](https://user-images.githubusercontent.com/108491443/196445353-e07cf17a-3e40-4cc4-85ea-47cfa39e5aac.png)

Este é um projeto do tipo insights, no qual, por meio de uma análise exploratória de dados, teve como objetivo gerar insights e recomendações de soluções para o problema de negócio em questão.


Para tal fim, o conjunto de dados utilizado foi obtido a partir do site [KAGGLE](https://www.kaggle.com/) e refere-se a diversos tipos de acomodações ofertadas por meio do Airbnb na cidade do Rio de Janeiro no período de 2019 a 2020.


![airbnb](https://user-images.githubusercontent.com/108491443/196446029-0b122bb3-4206-4dd2-b14d-53deb9b6c94c.png)

Segundo o seu próprio site, o Airbnb “começou em 2008, quando dois designers que tinham um espaço sobrando hospedaram três viajantes que procuravam um lugar para ficar. Agora, milhões de anfitriões e viajantes optam por criar uma conta gratuita no Airbnb para que possam anunciar seu espaço e reservar acomodações únicas, em qualquer lugar do mundo. Além disso, os anfitriões de experiências do Airbnb compartilham suas paixões e interesses com viajantes e moradores locais. O Airbnb ajuda a tornar o compartilhamento fácil, agradável e seguro. Verificamos perfis pessoais e anúncios, mantemos um sistema de mensagens inteligente para que anfitriões e hóspedes possam se comunicar com segurança e gerenciamos uma plataforma confiável para recolher e transferir pagamentos.”

Ou seja, Airbnb é um serviço online no qual facilita as pessoas a reservarem e alugarem meios de hospedagem de maneira mais segura e direta entre anfitriões e hóspedes. Podendo abranger diferentes tipos de acomodações, onde muitas vezes o preço chega a ser inferior aos dos hotéis e imóveis reservados por outros meios.

Fonte: [AIRBNB](https://www.airbnb.com.br/help/article/2503/o-que-%C3%A9-o-airbnb-e-como-ele-funciona)

___

Diante disso, foram formuladas indagações pertinentes a fim de direcionar o problema de negócio. Assim sendo, ao aplicar a análise exploratória de dados pretende-se responder a tais perguntas elaboradas, podendo gerar insights para investidores, anfitriões e viajantes.

O raciocínio utilizado para análise foi sistematizado em:

**Importação das bibliotecas e do dataset**

Foram empregues bibliotecas triviais para manipulação e visualização de dados. O dataset utilizado foi o listings

**Exploração do dataset**

Verificação do tamanho, colunas, tipos de dados, campos duplicados, valores nulos e estatísticas do dataset

**Limpeza dos dados:**

**Valores nulos**

O dataset apresentou-se com uma grande quantidade de valores nulos. Diante disso, primeiramente definiu-se a exclusão de todas as colunas que contivessem mais de 10%(3371.5 linhas) dos valores nulos. Assim, 33 colunas foram excluídas. Em seguida, foi feita uma leitura do dicionário dos dados a fim de excluir todas as colunas nas quais conjecturou em um primeiro momento serem irrelevantes para a questão de negócio, eliminando-se deste modo, mais 51 colunas, nas quais, algumas também continham valores nulos. Logo após, os valores nulos no restante das colunas que sobraram foram substituídos pela mediana nas variáveis numéricas e pela moda nas variáveis categóricas. OBS: escolheu-se a mediana em detrimento da média com o intuito de evitar outliers

**Outliers**

OBS: Outliers caracteriza-se por ser dados destoantes em comparação ao conjunto amostral.

Foi possível observar que eventos esportivos apareceram com certa frequência nas acomodações com os preços mais altos. Por serem fatos atípicos, e que ocorreram no passado em que os dados foram coletados, não representavam a realidade dos preços. Diante disto, foram excluídas do Dataset todas as linhas que estavam relacionadas a estes eventos.
Por meio da visualização de histogramas e Boxplots evidenciou-se a existência de muitos outliers, causando uma distorção na distribuição dos dados e consequentemente nas medidas de dispersão. 
Diante disso, foi utilizado o Intervalo Interquartil(IIQ) para remoção de outliers. O IIQ é uma medida de dispersão comumente representado por meio do gráfico de boxplot, este tipo de gráfico é utilizado para averiguar parâmetros e informações estatísticas a respeito dos dados como: valores máximo e mínimo, amplitude amostral, quartis, mediana e outliers. Por meio desses parâmetros, é possível ter uma concepção de que modo os dados estão distribuídos.

![boxplot3](https://user-images.githubusercontent.com/108491443/196447105-c7801b32-6eba-48cf-af22-aea00e62b260.png)

Cálculo do IIQ:

Primeiro quartil, 25% dos dados amostrais: Q1

Segundo quartil, 50% dos dados amostrais(Mediana): Q2

Terceiro quartil, 75% dos dados amostrais: Q3

Intervalo interquartil: IIQ = Q3 - Q1

Constante: c= 1,5

Limite inferior(Li): Li = Q1 - c * IIQ

Limite superior(Ls): Ls = Q3 + c * IIQ

Quaisquer valores abaixo do Limite inferior ou acima do Limite superior são considerados outliers, e foram removidos do dataset, tornando assim o conjunto de dados mais simétrico.

**Data visualization**

Em todas as perguntas de negócio que foram feitas buscou-se representar os dados através de diversos elementos visuais diferentes com a finalidade de respondê-las de forma elucidativa

**Conclusões finais**

Algumas percepções finais acerca do dataset e das perguntas feitas

**Insights**

Com base na análise exploratória dos dados foi possível listar alguns insights para a questão de negócio

**Referências**

Fontes nas quais contribuíram para a elaboração deste projeto

___

:hammer_and_wrench: **Tecnologias utilizadas**

Linguagem Python e suas bibliotecas, Jupyter Notebook

