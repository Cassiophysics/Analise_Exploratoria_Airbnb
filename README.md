
# Análise Exploratória de Dados - Airbnb RJ

![capa_airbnb](https://github.com/Cassiophysics/Analise_Exploratoria_Airbnb/assets/108491443/b1c5ee57-6d37-4fef-9b01-ca02d125ccb6)

Este é um projeto do tipo insights, no qual, por meio de uma análise exploratória de dados, teve como objetivo gerar insights e recomendações de soluções para o problema de negócio em questão.

Para tal fim, o conjunto de dados utilizado foi obtido a partir do site [KAGGLE](https://www.kaggle.com/) e refere-se a diversos tipos de acomodações ofertadas por meio do Airbnb na cidade do Rio de Janeiro no período de 2019 a 2020.

Segundo o seu próprio site, o Airbnb “começou em 2008, quando dois designers que tinham um espaço sobrando hospedaram três viajantes que procuravam um lugar para ficar. Agora, milhões de anfitriões e viajantes optam por criar uma conta gratuita no Airbnb para que possam anunciar seu espaço e reservar acomodações únicas, em qualquer lugar do mundo. Além disso, os anfitriões de experiências do Airbnb compartilham suas paixões e interesses com viajantes e moradores locais. O Airbnb ajuda a tornar o compartilhamento fácil, agradável e seguro. Verificamos perfis pessoais e anúncios, mantemos um sistema de mensagens inteligente para que anfitriões e hóspedes possam se comunicar com segurança e gerenciamos uma plataforma confiável para recolher e transferir pagamentos.”

Ou seja, Airbnb é um serviço online no qual facilita as pessoas a reservarem e alugarem meios de hospedagem de maneira mais segura e direta entre anfitriões e hóspedes. Podendo abranger diferentes tipos de acomodações, onde muitas vezes o preço chega a ser inferior aos dos hotéis e imóveis reservados por outros meios.

Fonte: [AIRBNB](https://www.airbnb.com.br/help/article/2503/o-que-%C3%A9-o-airbnb-e-como-ele-funciona)

___

## Motivação:

A motivação por trás da criação deste projeto de Análise Exploratória dos Dados do Airbnb na cidade do Rio de Janeiro é entender e aproveitar melhor as oportunidades oferecidas por essa plataforma de hospedagem. O Airbnb se tornou uma alternativa popular para viajantes que desejam experiências únicas e autênticas, e a cidade do Rio de Janeiro é um destino muito procurado.

Compreender o mercado de hospedagem do Airbnb no Rio de Janeiro é fundamental para proprietários de acomodações, gestores de propriedades, turistas e até mesmo para o planejamento urbano. Por meio da análise dos dados disponíveis, é possível obter insights valiosos sobre o perfil dos anfitriões, tipos de propriedades, preços, ocupação e preferências dos hóspedes.

O objetivo deste projeto é explorar os dados do Airbnb para gerar insights e recomendações que possam ajudar proprietários a melhorar a experiência dos hóspedes, ajustar preços de forma competitiva, identificar oportunidades de negócio e contribuir para um ecossistema de hospedagem mais eficiente e sustentável na cidade.

Ao disponibilizar esse projeto no GitHub, pretendo compartilhar os conhecimentos adquiridos e promover a colaboração com outros profissionais e entusiastas da área. Acredito que a análise exploratória dos dados do Airbnb no Rio de Janeiro pode fornecer informações valiosas para a tomada de decisões informadas e o desenvolvimento de estratégias bem fundamentadas no setor de hospedagem.

Sinta-se à vontade para explorar o código, os dados e as visualizações apresentadas neste repositório. Estou animado com os resultados obtidos e ansioso para ver como esse projeto pode evoluir e contribuir para uma experiência ainda melhor no Airbnb na cidade do Rio de Janeiro.

Diante disso, foram formuladas indagações pertinentes a fim de direcionar o problema de negócio. Assim sendo, ao aplicar a análise exploratória de dados pretende-se responder a tais perguntas elaboradas, podendo gerar insights para investidores, anfitriões e viajantes.

O raciocínio utilizado para análise foi sistematizado em:

## Importação das bibliotecas e do dataset:

Foram empregues bibliotecas triviais para manipulação e visualização de dados. O dataset utilizado foi o listings.

## Exploração do dataset:

Verificação do tamanho, colunas, tipos de dados, campos duplicados, valores nulos e estatísticas do dataset.

## Limpeza dos dados:

**Valores nulos**

O dataset apresentou-se com uma grande quantidade de valores nulos. Diante disso, primeiramente definiu-se a exclusão de todas as colunas que contivessem mais de 10%(3371.5 linhas) dos valores nulos. Assim, 33 colunas foram excluídas. Em seguida, foi feita uma leitura do dicionário dos dados a fim de excluir todas as colunas nas quais conjecturou em um primeiro momento serem irrelevantes para a questão de negócio, eliminando-se deste modo, mais 51 colunas, nas quais, algumas também continham valores nulos. Logo após, os valores nulos no restante das colunas que sobraram foram substituídos pela mediana nas variáveis numéricas e pela moda nas variáveis categóricas. OBS: escolheu-se a mediana em detrimento da média com o intuito de evitar outliers.

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

## Data visualization:

Em todas as perguntas de negócio que foram feitas buscou-se representar os dados através de diversos elementos visuais diferentes com a finalidade de respondê-las de forma elucidativa.

## Perguntas elaboradas e respostas encontradas:

### 1- Quais são os tipos de acomodações mais ofertadas e quais possuem maior faturamento?
- Apartamento é o tipo de acomodação mais comum no Rio de Janeiro e o que apresenta maior faturamento;
- Cabana é a que possui maior preço médio.

### 2- Quais são os Top 10 acomodações mais caras e mais baratas?

**R:** 

### 3- Quais bairros apresentam a maior quantidade de acomodações e quais possuem maior faturação total?
- Barra de Tijuca é o bairro que possui a maior quantidade de acomodações e a maior receita.

### 4- Qual a faixa de preço mais popular e qual a que possui a maior receita?
- Embora a quantidade de acomodações com a faixa de preço em barato seja a mais popular, é a que têm a menor receita;
- A faixa de preço caro é a que possui maior receita total.

### 5- Superhosts, Hosts verificados e Hosts com maior quantidade de anúncios possuem maior valor total faturado?
- A quantidade de Superhosts é muito pequena, o que pode indicar que Superhost não seja um atributo tão simples de se conquistar. Assim, em razão da parcela diminuta de Superhosts, a receita total com esta característica também tende a ser menor.

- Existe uma maior quantidade de hosts que não possuem verificação do que hosts com verificação; A receita total de hosts não verificados é bem maior; A diferença entre a média dos preços de hosts verificados e não verificados não é significativa.

- Mais da metade dos Hosts possuem apenas um anúncio; Surpreendentemente Hosts com menor quantidade de anúncios dispõem de maior receita. Logo, ao que tudo indica, uma maior quantidade de anúncios não gera impacto significativo sobre a receita total.

### 6- Qual o comportamento do preço pela quantidade de banheiros, quartos, camas e por tipos diferentes de quartos e camas?
- Acomodações com somente um banheiro são as mais frequentes e com maior arrecadamento; O preço médio tende a aumentar à medida em que o número de banheiros aumenta.

- Acomodações com apenas um quarto são as mais listadas e que possuem maior faturação; Existe uma tendência no aumento do preço médio ao passo em que o número de quartos também aumenta; Acomodações no qual a quantidade de quartos é zero, possivelmente representem acomodações em que o quarto, cozinha, sala e demais áreas existentes são combinados em um único espaço aberto, não havendo uma delimitação concreta separando o quarto dos demais cômodos.

- Espaço inteiro é o tipo que quarto que aparece em maior frequência, tem maior preço médio e maior receita.

- As acomodações mais comuns são as que contam com apenas uma cama; O preço médio tem uma certa tendência em aumentar com a quantidade de camas; A receita total tende a ser maior quanto menor for o número de camas.

- Acomodações com cama real são as mais habituais e apresentam maior receita total; Acomodações com sofá possuem maior preço médio.

### 7- Acomodações que apresentam maior quantidade de avaliações, capacidade de hóspedes e convidados inclusos possuem vantagens na receita total?
- Existe uma quantidade significativa de acomodações sem avaliações; Quantidade de avaliações apontam não ter influência sobre o preço.

- Acomodações com capacidade de 2 e 4 hóspedes são as mais usuais e possuem maior receita; O preço médio tende a aumentar conforme a capacidade de hóspedes também aumenta.

- Acomodações com apenas um convidado incluso são as mais presentes, com maior preço médio e faturamento.

### 8- Acomodações com reserva instantânea apresentam maior ganho? Qual o número de pernoites mais ofertado?
- Mais da metade das acomodações não possuem reserva instantânea; Acomodações com reserva instantânea têm uma receita total menor; Não existe uma diferença expressiva entre o preço médio em acomodações que possuem reserva instantânea de acomodações que não possuem reserva instantânea.

- Acomodações com menor número de pernoites são as mais ofertadas e as que possuem maior renda total; O preço médio tem uma certa propensão em aumentar conforme o número de pernoites também aumenta.

### 9- Qual a proporção de acomodações que oferecem o serviço de hóspedes extras? E qual o preço médio?
- A grande maioria das acomodações está com o preço de hóspedes extras a zero reais, talvez isto possa indicar que a maior parte das acomodações não oferecem este serviço;
- Das acomodações que possivelmente oferecem este serviço, a média de preço é 62 reais, com preços de 50 e 100 reais sendo os mais frequentes e com maior ganho financeiro.

### 10- Quais fatores mais influenciam no preço?
- Capacidade de hóspedes, quartos, banheiros, camas e mínimo de pernoites identificaram-se como tendo as maiores correlações com preço.

## Conclusões finais:

Algumas percepções finais acerca do dataset e das perguntas feitas:

- O conjunto de dados apresentou um grande número de colunas com valores nulos.
- As acomodações relacionadas a eventos esportivos passados, como a Copa do Mundo de 2014 e as Olimpíadas do Rio 2016, apresentaram valores extremamente altos.
- Foi observada uma quantidade excessiva de outliers, afetando diretamente a distribuição das colunas quantitativas.
- Embora fosse esperado que os Superhosts, Hosts verificados e Hosts com maior quantidade de anúncios obtivessem vantagens lucrativas em relação aos demais, a maioria dos Hosts não possuía essas características e ainda assim obtiveram maiores lucros. Isso pode indicar uma falta de profissionalismo por parte dos anfitriões ou que os hóspedes não consideram esses atributos ao escolher uma acomodação.
- Foi identificado um grande número de acomodações sem avaliações, indicando que isso não é relevante para os hóspedes.
- A diferença no preço médio entre as acomodações com reserva instantânea e as sem reserva instantânea não é significativa. No entanto, mais da metade das acomodações não possui reserva instantânea e são essas que têm maior receita total. Isso sugere que a reserva instantânea não é essencial para anfitriões e hóspedes.
- Foi observado que o preço médio tende a aumentar à medida que o número de banheiros, quartos, camas, capacidade de hóspedes, convidados inclusos e número de pernoites aumentam.
- Uma proporção considerável de acomodações não oferece o serviço de hóspedes extras.

## Insights:

Com base na análise exploratória dos dados foi possível listar alguns insights para a questão de negócio. Os seguintes critérios foram identificados como os mais rentáveis. Com base nisso, uma estratégia promissora seria investir em:

- Acomodações do tipo apartamento.
- Acomodações localizadas no bairro Barra da Tijuca.
- Acomodações com faixa de preço alta (301 a 500 reais).
- Acomodações com apenas um banheiro, um quarto e uma cama, onde o tipo de quarto é "espaço inteiro" e o tipo de cama é "real".
- Acomodações com capacidade para 2 e 4 hóspedes.
- Acomodações com apenas um convidado incluso.
- Acomodações com um número baixo de pernoites para reserva.
- Acomodações com preço de hóspedes extras de 50 e 100 reais.
- Acomodações próximas ao mar.

## Impacto nos negócios:

A análise dos dados do Airbnb pode oferecer benefícios financeiros e de negócios, incluindo:

**Otimização de preços:** Identificar padrões de preços e demanda para ajustar estratégias de precificação e maximizar a receita.

**Melhoria da ocupação:** Compreender os fatores que influenciam a ocupação para otimizar propriedades e atrair mais hóspedes.

**Identificação de oportunidades de investimento:** Identificar áreas com alta demanda e baixa oferta para oportunidades de investimento imobiliário.

**Melhoria da experiência do cliente:** Utilizar avaliações e feedbacks dos hóspedes para aprimorar a limpeza, conforto e comodidades, aumentando a satisfação e a fidelidade.

**Tomada de decisões estratégicas:** Aproveitar insights para definir estratégias de marketing, identificar segmentos promissores e maximizar os resultados.

## Identificação de melhorias para o projeto:

**Aumentar a quantidade de dados:** Se possível, buscar e utilizar um conjunto de dados mais abrangente e representativo. Quanto mais dados disponíveis, mais robusta e confiável será a análise exploratória.

**Realizar análises mais avançadas:** Além da análise exploratória básica, considerar a aplicação de técnicas mais avançadas, como modelagem estatística, aprendizado de máquina ou mineração de dados, para descobrir padrões mais complexos e obter insights adicionais.

**Incorporar dados externos:** Além dos dados do próprio Airbnb, considerar a inclusão de dados externos relevantes, como informações sobre eventos culturais, transporte público, infraestrutura turística e índices econômicos. Esses dados adicionais podem enriquecer a análise e fornecer insights mais abrangentes.

**Aprofundar a análise por regiões:** Em vez de considerar apenas a cidade do Rio de Janeiro como um todo, aprofundar a análise por bairros ou regiões específicas. Isso permitirá identificar diferenças nas preferências dos hóspedes, padrões de preços e demanda por diferentes áreas da cidade.

**Incorporar técnicas de visualização de dados interativas:** Utilizar ferramentas de visualização de dados interativas, como gráficos interativos, para melhorar a apresentação dos resultados e facilitar a exploração dos dados pelos usuários.

**Realizar análises comparativas:** Comparar a performance das acomodações no Rio de Janeiro com outras cidades ou regiões semelhantes. Isso pode fornecer insights sobre a competitividade das acomodações oferecidas na cidade e ajudar a identificar áreas de oportunidade ou desafios específicos.

**Considerar feedback dos usuários:** Buscar feedback e opiniões de usuários do Airbnb no Rio de Janeiro para entender suas necessidades, desejos e experiências. Isso pode ser feito por meio de pesquisas, entrevistas ou análise de comentários e avaliações deixados pelos hóspedes.

**Atualizar regularmente a análise:** À medida que novos dados se tornam disponíveis ou as condições do mercado mudam, é importante atualizar regularmente a análise exploratória para garantir que as recomendações e insights sejam relevantes e atualizados.

___

## 🗺️ Renderização dos Mapas <h2>

Alguns mapas não são renderizados no Github, para uma visualização completa: https://nbviewer.org/github/Cassiophysics/Analise-Exploratoria-Airbnb-RJ/blob/main/Analise-Exploratoria-Airbnb-RJ.ipynb
  


