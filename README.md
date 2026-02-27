# Projeto de Pesquisa   

Aluno(a): Leonardo Takashi Teramatsu
Orientador(a): Prof. Dr. Miguel Ângelo Lellis Moreira 
Curso: MBA em Data Science e Analytics

## Título do Projeto de Pesquisa

> Estabilidade de Features Clássicas na Detecção de Phishing: Análise Cross-Dataset com Logistic Regression e Random Forest

## Introdução 

Phishing constitui uma ameaça sistêmica em cibersegurança contemporânea, caracterizada pela combinação de engenharia social e tecnologia computacional para apropriação fraudulenta de informações sensíveis. Formalmente, phishing é definido como um ataque de rede que explora quatro dimensões críticas: deception (falsificação de identidade de entidades legítimas), impersonation (personificação de marcas, instituições financeiras ou autoridades), scalability (capacidade de disseminação massiva via e-mail, SMS ou redes sociais) e human vulnerability (exploração de vieses cognitivos e falhas de julgamento humano) Alkhalil Z (2021) [1]. Esta definição multidimensional evidencia que phishing transcende vulnerabilidades técnicas, operando primariamente na interface entre sistemas computacionais e comportamento humano.

A magnitude econômica do problema é substancial e crescente. Em 2014, a capitalização de mercado associada a perdas por phishing foi estimada em US$ 330 milhões, refletindo o impacto direto em instituições financeiras e organizações corporativas [2]. Dados subsequentes do Federal Bureau of Investigation (FBI) dos Estados Unidos documentaram perdas de US$ 2 bilhões em 2018 envolvendo phishing direcionado a bancos e plataformas de câmbio digital, escalando para US$ 1,6 milhões em 2019 e US$ 4,7 bilhões em 2021 [3]. O Anti-Phishing Working Group (APWG) reportou crescimento exponencial no volume de ataques: de 44.008 e-mails de phishing no primeiro trimestre de 2020 para 128.926 no terceiro trimestre do mesmo ano, representando aumento de 193% em seis meses [3]. Estes indicadores quantitativos demonstram não apenas a persistência da ameaça, mas sua aceleração em escala e sofisticação, consolidando phishing como vetor de ataque prioritário em estratégias de defesa cibernética.  aceleração em escala e sofisticação, consolidando phishing como vetor de ataque prioritário em estratégias de defesa cibernética.

A literatura contemporânea em detecção de phishing apresenta lacunas metodológicas críticas que comprometem a generalização e aplicabilidade prática de modelos propostos.

Foi identificado, Taha et al. (2024) [18], que Logistic Regression (LR), Random Forest (RF) e XGBoost constituem baselines robustos com acurácia de 85-95% em datasets padronizados, oferecendo três vantagens críticas: 

- interpretabilidade via SHAP (SHapley Additive exPlanations), permitindo auditoria de decisões e conformidade regulatória; 
- aplicabilidade de Permutation Feature Importance (PFI), para obtencao das features relevantes de um Dataset A e realizar uma avaliacao cruzada com o Dataset B e, com a aplicacao de SHAP, na tentativa de explicar o motivo de tais features serem, possiveis candidatos estaveis;
- custo computacional reduzido, viabilizando execução em CPU sem dependência de GPU ou, caso dependa, em quantidade a nivel inconveniente da maioria dos usuarios cotidianos nao conseguirem arcar com os custos; 
- manutenção simplificada, com ciclos de re-treinamento menos frequentes e com a expectativa de menor sensibilidade a concept drift [3]. 

Segundo o Tang, L. [3], a seleção de recursos é o processo de selecionar automaticamente os recursos importantes que mais contribuem para o modelo de aprendizado de máquina. Ter recursos altamente relevantes na entrada pode melhorar o desempenho do modelo, diminuir o tempo de treinamento (especialmente em modelos de aprendizado profundo) e reduzir problemas de sobreajuste. Logo, ela exerca uma funcao crucial no processo de generalizacao dos modelos preditivos a nivel de nao ficar doutrinado sobre um determinado tipo de conjunto de dados, de modo a ser possivel realizar uma analise preditiva otimizada para um outro tipo de conjunto de dados tambem. Portanto, encontrar aquelas features estaveis que tenham a capacidade de transcender a dependencia dos conjuntos de dados, seriam as features bastante relevantes para otimizacao das generalizacoes e da previsoes dos modelos preditivos. Alem disso, ao analisar as literaturas que representem os estados de artes para a deteccao de Phishings, percebe-se, em muitas delas, focadas em estudos comparativos dos modelos que melhor obtiveram a precisao nas suas previsoes, porem, poucos estudos procuram tentar entender os motivos e as limitacoes de tais resultados metricos exibidos pelos modelos, a partir de um conjunto de dados e, dentro das literatuas que o autor deste projeto de pesquisa conseguiu analisar, nao se encontrou nenhum estudo sobre a obtencao de tais features estaveis e que, ao mesmo tempo, que sejam capazes de explicar o motivo de tais features, caso exista, serem importantes para otimizacao das deteccoes de Phishings e, muito menos, na obtecao do numero minimo a nivel axiomatico que sustentaria toda a base para otimizacao das deteccoes de golpes no geral. Claro, existem tecnicas, como RFE (Recursive Feature Elimination), que consiste em reduzir os numeros de features consideradas menos importantes, porem, utilizando com base nas metricas probabilisticas com ausencia explicativas para tais obtencoes e reducoes das features sobre um determinado conjunto de dados. Dado que o golpe Phishing ela possui uma natureza classificatoria, existem outras tecnicas como PCA (Principal Components Analysis), IG (Information Gain), FRS (Fuzzy Rough Set), RS (Rough Set) e uma tecnica inovadora apresentada pelo El-Rashidy (2021) [28] que utiliza o modelo, Random Forest, para realizar tais selecoes em duas etapas, onde tais tecnicas, muitas vezes, sao utilizadas como uma justificativa do que mostra tais relevancia para as features extraidas sobre um determinado tipo de conjunto de dados, D. P. Garapati (2024) [21], o que, do ponto de vista empirico possui grande relevancia teorica e aceita pela comunidade cientifica no ramo de Ciencias de Dados. Porem, do ponto de vista de uma definicao matematica a nivel de conseguir demonstrar teoricamente a importancia disso, em todas elas, ha ausencia de alguma interpretabilidade/explicabilidade sobre o motivo de tais parametros serem essenciais e se elas serao ou nao estaveis a nivel de formalidade possivel de ser demonstrado, matematicamente, de fornecer uma explicacao plausivel a nivel de enxergar as suas limitacoes, caso utilizado para o ajuste fino em modelos preditivos e realizado as devidas inferencias e cruzamento de um outro conjunto de dados.

Por exemplo, Taha et al. (2024) [18] estabeleceram benchmarks quantitativos no dataset "Phishing Websites Dataset" obtido pelo site Kaggle (N=11.055 URLs amostras balanceadas): 

- Logistic Regression alcançou F1-score de 0,92 e acurácia de 0,93, dentre os sites consideradas Phishings;
- Random Forest superou estas métricas com F1-score de 0,97 e acurácia de 0,97, dentre os sites consideradas Phishings.

A analise acima, decorre, apenas, de um conjunto de dados, cuja composicao sua eh feita de PhishTank e Alexa. E o estudo acima foi focado na parte comparativa entre 5 modelos:

- Logistic Regression
- Random Forest
- Decision Trees
- Adaptative Boosting
- XGBoost

Entretanto, nao foi identificado, dentro desses comparativos, aquelas features que continuam relevantes para compor como uma parte do parametro padrao que sirva para aqueles modelos que sejam candidatos fortes para o uso preditivo como Logistic Regression, Random Forest e XGBoost. Embora, que tais modelos ja se mostram fortes candidatos a usos reais em entidades institucionais ou organizacionais, mesmo que, ainda, apresentem desafios significativos no ambito socio-tecnico quando se trata de definir protocolos ou normas de condutas aplicados sobre os fatores humanos, de modo que nao comprometam na produtividade devido a necessidade de uma demanda de uma carga cognitiva desnecessaria, ou da capacidade das adaptabilidades dos modelos preditivos que nao demandem altos custos aquisitivos para as entidades institucionais ou organizacionais.

Uma investigacao comparativa e, muito proxima, do que esta sendo proposto dentro desse projeto de pesquisa foi feita pelo Y. Ari Kustiawan (2025) [19]. Porem, novamente, o estudo focou, dentro de tres tipos de datasets como PhishTank, OpenPhish e Open PageBank, na tentativa de aumentar o numero de categorias em que poderia ser extraido as features, que antes eram limitados em URL e HTML, incluindo a terceira categoria "features derivados". A investigacao, no entanto, terminou em realizar, novamente, os mesmos comparativos que foram feitas em Taha et al. (2024) [18] nao realizando o que estou propondo sobre tentar extrair e analisar o motivo da relevancia dos numeros minimos de features que seriam necessarias, a partir de um conjunto de datasets heterogeneos que os torna uniforme a nivel de ser considerado como um requisito necessario a ser considerado ao ser considerado como os parametros de ajuste finos nos modelos leves e que sao fortes candidatos a conseguir realizar as devidas predicoes.

O mesmo padrao de analise comparativa foi observado para os estudos como Singh, Preet (2024) [20], Seksit Prakongsin (2025) [22] e D. P. Garapati (2024) [21]. Dentro dos estudos recentes e que fazem parte dentro das classes que representam os estados de artes voltado a melhoria na eficiencias preditivas, porem, nenhuma delas realizando alguma analise na obtencao das features estaveis que transcendem os tipos de datasets de modo que sirvam de parametros padroes para os modelos candidatos fortes para predicoes.

Alem disso, enquanto foi apresentado os estudos acima focado para melhorar a precisao e eficiencias das previsoes dos modelos, um outro fator que, ate entao, nao havia sido investigado seria na capacidade de explicar o motivo daquelas previsoes serem eficientes por quais motivos. Um estudo antigo feito pelo LUNDBERG, S. M (2017) [12], tentou investigar para encontrar alguma solucao perante a lacuna que foi apontado sobre a explicabilidade das previsoes dos modelos. Na tentativa de sanar o problema, o metodo que foi aplicado, na tentativa de obter alguma explicacao conveniente do motivo da previsao feita pelos modelos, se chama SHAP (SHapley Additive exPlanations), onde ela eh uma tecnica voltado para possibilitar em entender o motivo das previsoes e as limitacoes que os modelos possuem perante aos resultados das previsoes. Os seus componentes inovadores incluem:

- a identificação de uma nova classe de medidas de importância de características aditivas;
- resultados teóricos que mostram que há uma solução única nessa classe com um conjunto de propriedades desejáveis.

O que foi visto como algo bastante promissora e, ao mesmo tempo, componentes desejaveis, visto os estudos comparativos de modelos carecem desses tipos de analise. Porem, como foi comentado com base nos estudos comparativos anteriores, nenhuma delas, dentro das metricas foi aplicado tal metodo na tentativa de explicar o motivo da previsao ter sido precisa focando, apenas, na melhora da precisao. Muito menos, no artigo que implementa o SHAP, nao foi feito algum estudo focado em investigar quais os tipos de features estaveis, que sera a proposta deste projeto, este artigo foca, somente, em mostrar as bases matematicas que focam o que indica na interpretabilidade das relevancias das features.

Alem disso, no estudo de um levantamento mais recente que foi encontrado sobre a capacidade de explicabilidade foi feito pelo Haiyan Zhao (2024) [5]. Nela, foi mostrado uma anatomia que mostra as subdivisoes onde seria possivel a aplicaao de explicabilidade e, dentro dessas subdivisoes, reside a parte onde esse projeto de pesquisa esta focado que seria na obtencao de features estaveis para utilizacao de tais parametros no momento em que for realizar os ajustes finos.

Porem, o SHAP (https://shap.readthedocs.io/en/latest/generated/shap.Explainer.html), sera utilizado nesse projeto, visto que ela possui a seguinte relevancia:

- SHAP ela esta voltado para parametros menores. Ou seja, se aplicada para parametros na casa dos bilhoes, ela exige um consumo computacional substancial.
- para tentar obter e entender as features estaveis, podemos utiliza-la por meio do entendimento do motivo do modelo ter se comportado de tal forma, apos feito o ajuste fino com tais features, e ter obtido tais previsoes. E disso, ir tentando obter as devidas features estaveis e desejaveis.
- a nivel de obter as features estaveis para otimizar as deteccoes de Phishings com recursos computacionais baratos, acabam sendo convenientes.
- SHAP eh compativel para os modelos de aprendizagem que sera abordado para esse projeto.

Novamente, segundo o Tang, L. [3], uma outra forma de conseguirmos impor relevancia nas features seria vinda de uma tecnica chamado Feature Importance desenvolvido pelo Gupta et al. em 2021, que possibilitou em atingir a precisao do modelo, Random Forest, em 99.57%. Tal experimento foi aplicado sobre o conjunto de dados ISCX-URL-2016, publicado pela Universidade de Brunswick no Canada. Esse conjunto de dados, ISCX-URL-2016, contem mais de 35300 URLs legitimos e, aproximadamente 10000 URLs de phishings retirados de um repositorio ativo de sites de phishing, https://openphish.com/, que segue em constante atualizacao. Porem, novamente, esse estudo ainda nao abordou sobre features estaveis de modo a realizar testes com conjunto de dados de Phishing diferentes das que foi pega. Porem, para o nosso proposito no projeto, combinado com o SHAP, foi visto pelo autor do projeto alguma possibilidade de que a combinacao dessas duas tecnicas possa trazer alguma pista promissora para conseguir obter algum resultado que possa trazer o primeiro passo para a obtencao de features estaveis e, se possivel, posterior formalizacao teorica que possibilita a explicacao do motivo dessas features estaveis, de fato, ser um requisito necessario a ser incluso para obter um bom grau de generalizacao aos modelos preditivos. O estado de arte dessa tecnica envolve a aplicacao do conceito chamado Permutation Feature Importance, aplicado pelo A. Khan (2025) [29], no qual, devido aos custos computacionais altos que eram demandados pelo treinamento automatizado para manter ou melhorar os desempenhos dos modelos de maquina de aprendizagens, foi visto a necessidade desenvolver ou combinar alguma tecnica para reduzir tais custos e, ao mesmo tempo, que nao impacte tanto na diminuicao do desempenho nas previsoes dos modelos preditivos. As features selecionadas foram utilizadas para retreinar os modelos de Maquinas de Aprendizagem sem hiperparâmetros (configurações padrão) para determinar se um desempenho semelhante poderia ser alcançado com baixo custo computacional. Os resultados dessa pesquisa mostraram uma melhoria média de precisão de 77,39% e uma redução de 92,02% no custo computacional. O caso mais importante alcançou uma melhoria de 99,25% na precisão e uma redução de 96,77% no custo, de modo a comprovar que o PFI seja um forte candidato a ser aplicado nesse projeto de pesquisa.

A relevância da estabilidade de features transcende questões metodológicas, impactando diretamente viabilidade operacional de sistemas de detecção. Transferibilidade de modelos depende de features que mantenham poder discriminativo em contextos distintos (diferentes provedores de e-mail, domínios geográficos, períodos temporais), permitindo deploy sem necessidade de re-treinamento completo.

Claro, nao esta sendo negligenciado a importancia de uma boa selecao de um conjunto de dados para realizar uma boa extracao de features e que, por ventura, isso poderia contribuir para obtencao mais rapida de tais features estaveis. Porem, visto a natureza bastante incerta dentro do campo de golpes, conforme o surgimento de novas tecnologias que sustentam uma boa parte da rotina das pessoas, as dificuldades em aumentar tais previsoes e os custos que sao arcados para a construcao e manutencao das infra-estruturas, por mais que sejam flexiveis e adaptaveis a novos cenarios de ataques, ainda continuam sendo bastante altos. Logo, conseguir obter alguma tecnica que permite obter features mais estaveis de maneira rapida com base das previsoes, poderia contribuir em aumentar as chances de impedir que novos vetores de ataques consigam se bem susceder ou, pelo menos, diminuir o impacto que esse novo vetor de ataque poderia ocasionar de prejuizo para a entidade legal e, ao mesmo tempo, conseguir diminuir os custos aquisitivos que tais entidades legais precisariam arca-las. Alem disso, com a expectativa de que o desenvolvimento de tais tecnicas de obtencao de features estaveis, se possivel, servir como uma pista para obter uma alguma definicao mais formal e teorica do que seria o conceito de explicabilidade a nivel de formalidade matematica, de modo que se torne o suficiente para conseguir clarificar mais ainda a velha caixa preta que esta bastante ofuscada sobre os modelos complexos que existem em LLMs. Logo, como um primeiro passo disso, como uma via introdutoria, foi pensado a possibilidade de realizar alguma analise combinando as duas tecnicas, a nivel de analisar a transferabilidade das features: Permutation Feature Importance e SHAP.

Um ponto em que precisamos deixar bem claro, seria que esse problema que esta sendo investigado e que sera abordado ao longo desse projeto de pesquisa nao eh transferencia de aprendizado, como explicado de forma didatica em Pan, Sinno (2010) [8]. O projeto foca a um passo atras desse conceito. Ou seja, ela foca em avalizacao de cruzamento de dados ou, equivalentemente, analise de transferibilidade das features. Logo, utilizaremos os tres modelos mencionados acima, nao para realizar um aprendizagem por transferencia, mas, sim, para tentar obter tais features estaveis, ao realizar os cruzamentos de dados por intermedio de cada modelo. Ou seja, pegamos o dataset A e, realizamos a extracao das features utilizando os modelos. Para cada modelo sera obtido as respectivas features e, em seguida, treinamos cada um dos modelos com os seus respectivos features extraidas, e realizamos uma inferencia com o dataset B e vice-versa. E do resultado da inferencia e predicao obtida, dela, aplicamos o SHAP para obter alguma explicacao plausivel e clara para tentar encontrar alguma perspectiva para refinar mais ainda as selecoes das features.

Questão Central: Quais features clássicas de phishing (URL e texto) apresentam estabilidade estrutural quando modelos Logistic Regression e Random Forest são transferidos entre datasets públicos heterogêneos (Cross-Data evaluation) (PhishTank e UCI) sem re-treinamento? 

Questões Derivadas: 

- QD1: Qual a importância relativa de 20 features clássicas (10 URL + 10 texto) segundo Permutation Feature Importance e SHAP TreeExplainer no dataset PhishTank (N=10.000)?
- QD2: Qual a correlação de Spearman (ρ) entre rankings de importância de features em PhishTank versus UCI [3], e qual a degradação de AUC (ΔAUC) na transferência sem re-treinamento?
- QD3: Qual conjunto mínimo robusto de 15-20 features (redução de 50-60%) mantém performance aceitável (F1-score ≥0,85, AUC ≥0,90) em ambos os datasets?

O processo de coleta de dados e extracao de features Embora não represente inovação disruptiva, o estudo preenche vazio metodológico ao operacionalizar recomendações de Tang & Mahmoud (2021) [3] para avaliação de transferibilidade, interpretabilidade e robustez temporal. O protocolo de 10 passos experimentais é replicável, emprega datasets públicos (PhishTank, UCI), e utiliza métricas quantitativas padronizadas.

Criterio de selecao das features:

- El-Rashidy (2021) [28];

Criterio de avaliacao das importancia das features selecionadas:

- Permutation Feature Importance para entender quais features sao fortemente dependentes;
- SHAP para responder o quanto dessas features dependentes contribuiram para a predicao/inferencia.

Metricas de avaliacao:

- Spearman ρ segundo Cohen 1988 [6],
- ΔAUC e Bootstrap IC 95% segundo Efron & Tibshirani 1993 [7] e Kohavi, Ron (2001) [10].

E com base disso, iremos obter as metricas:

- Accuracy, 
- Precision, 
- Recall, 
- F1-Score.

Feito os passos acima, iremos, por fim, realizar uma analise qualitativa das estabilidades das features sobre os cruzamentos dos datasets.

Protocolo replicável de analise de transferibilidade sem re-treinamento, seguindo framework de Pan & Yang (2010) [8]:

- 2 datasets públicos, eliminando necessidade de coleta manual ou parcerias institucionais; 
- 20 features clássicas;
- 2 modelos (LR, RF e XGBoost), focando em baselines interpretáveis;
- 2 métricas de estabilidade (Spearman ρ, ΔAUC), simplificação em relação a análise multidimensional (Kendall τ, Jaccard, Bootstrap 1.000 iterações).

## Objetivo

> Investigar a consistência de features clássicas de phishing entre datasets públicos heterogêneos (PhishTank e UCI) mediante análise de importância via SHAP TreeExplainer e Permutation Feature Importance, quantificando estabilidade via correlação de Spearman (ρ), degradação de AUC (ΔAUC) e Bootstrap, com vistas a identificar subconjunto mínimo robusto de atributos transferíveis entre contextos distintos.

- OE1: Quantificar importância de 20 features clássicas (10 URL + 10 texto) via SHAP TreeExplainer e Permutation Importance em Dataset A (PhishTank, N=10.000, balanceado 50/50 phishing/legítimo), estabelecendo ranking de contribuição para modelos Logistic Regression, Random Forest e XGBoost. 
- OE2: Avaliar transferência de modelos Logistic Regression (LR), Random Forest (RF) e XGBoost treinados em Dataset A (PhishTank) para Dataset B (UCI, N=11.055, balanceado 50/50) sem re-treinamento, calculando: 
    - (i) correlação de Spearman (ρ) entre rankings de importância de features nos dois datasets, interpretada segundo Cohen (1988) como estável (ρ>0,7), moderada (0,5≤ρ≤0,7) ou instável (ρ<0,5) [6];
    - (ii) degradação de AUC (ΔAUC), definida como |AUC_A - AUC_B|, interpretada como boa (ΔAUC<0,05), moderada (0,05≤ΔAUC≤0,10) ou severa (ΔAUC>0,10).
    - **(iii) Bootstrap, a explicar...**
- OE3: Identificar features estruturalmente estáveis (ρ>0,7, degradação <10%) versus instáveis (ρ<0,5), propondo conjunto mínimo robusto de 15-20 features (redução de 50-60% em relação a conjuntos típicos de 40-50 features) que mantenha performance aceitável (Accuracy, Precision, Recall,F1-score ≥0,85, AUC ≥0,90) em ambos os datasets.

## Metodologia ou Material e Métodos

A estratégia experimental fundamenta-se na seleção intencional de dois datasets públicos heterogêneos que simulam condições realistas de transferibilidade.

### DataSets

#### PhishTank
PhishTank é um repositório comunitário mantido por crowdsourcing que agrega e verifica URLs de phishing reportadas por usuários globalmente, constituindo fonte padrão na comunidade de pesquisa em cibersegurança Tang, L (2021) [3]. Para este estudo, foi selecionada amostra de N=10.000 instâncias balanceadas (5.000 phishing + 5.000 legítimas), coletadas no período 2023-2024, garantindo representatividade temporal recente e equilíbrio de classes que elimina viés de desbalanceamento. A escolha de PhishTank como Dataset A (treinamento) justifica-se por três razões:

- atualidade temporal, refletindo táticas de ataque contemporâneas; 
- diversidade geográfica, com URLs reportadas de múltiplos continentes e idiomas; 
- heterogeneidade de fontes, incluindo e-mails, SMS, redes sociais e anúncios maliciosos, simulando variabilidade de vetores de ataque em ambientes reais. 

#### UCI
UCI Machine Learning Repository mantém dataset curado de phishing com N=11.055 instâncias balanceadas (5.527 phishing + 5.528 legítimas), coletadas no período 2016-2020, amplamente utilizado como benchmark em pesquisa acadêmica Tang, L (2021) [3]. A escolha de UCI como Dataset B (teste de transferência) justifica-se por três razões:

- heterogeneidade temporal (diferença de 7 anos versus PhishTank 2023-2024, simulando concept drift natural); 
- diversidade de fonte (dataset acadêmico curado versus crowdsourcing comunitário); 
- disponibilidade de benchmarks (Taha 2024), permitindo comparação quantitativa de resultados.

### Maneiras de extracoes:
Será necessário extrair um conjunto de 20 features padronizadas (10 relacionadas à URL e 10 ao conteúdo textual), de modo a permitir a modelagem preditiva e a análise interpretável do problema.

A extração deverá empregar bibliotecas consolidadas do ecossistema Python, garantindo reprodutibilidade, robustez estatística e compatibilidade com pipelines de Machine Learning:

- scikit-learn: para vetorização TF-IDF e padronização (StandardScaler); 
- tldextract: para parsing estruturado de domínios; 
- NLTK: para tokenização e métricas lexicais; 
- requests: para análise de redirecionamentos HTTP; 
- BeautifulSoup: para parsing estrutural de HTML; 
- APIs WHOIS: para metadados de domínio.

O objetivo desta etapa é estruturar variáveis com poder discriminativo suficiente para capturar padrões característicos de phishing documentados na literatura recente.
 
A extração dessas features é necessária para construir representações estruturadas compatíveis com modelos supervisionados (ex.: Logistic Regression, Random Forest e XGBoost), permitir análise interpretável posterior (ex.: SHAP), fundamentar a modelagem em evidências empíricas da literatura recente e reduzir dependência exclusiva de modelos puramente end-to-end baseados em embeddings.

Serão implementados dois modelos clássicos de machine learning, selecionados com base em três critérios técnicos:

- Alta interpretabilidade, essencial para análise posterior de importância de variáveis;
- Baixo custo computacional, permitindo execução eficiente em CPU;
- Validação consolidada na literatura, com benchmarks estabelecidos em datasets de phishing.

Os modelos escolhidos serão:

- Logistic Regression (LR)
- Random Forest (RF)
- XGBoost

Configuração inicial planejada:

- penalty='l2' (regularização L2),
- C=1.0 (inverso da força de regularização),
- solver='lbfgs' (otimizador quasi-Newton),
- max_iter=1000.

### Justificativa técnica das escolhas dos modelos:

#### Logistic Regression
A regressão logística é uma técnica popular utilizada para tarefas de classificação binária, na qual modela a probabilidade de um resultado pertencer a uma das duas classes. É frequentemente empregada em problemas de aprendizado de máquina envolvendo classificação binária, onde o objetivo é dividir os dados em um dos dois grupos com base em um conjunto de características. Com base nas variáveis independentes fornecidas, o modelo de regressão logística usa uma função sigmoidal ou logística para prever a probabilidade de que a variável dependente seja 1. A função sigmoidal mapeia entradas com valores reais para um intervalo de 0 a 1, representando a probabilidade. O algoritmo de regressão logística utiliza a estimativa de máxima verossimilhança para estimar os coeficientes das variáveis independentes. Esses coeficientes são então usados para calcular a probabilidade da variável dependente ser 1 com base nos dados de entrada. Na prática, a regressão logística pode ser aplicada a uma variedade de aplicações, como pontuação de crédito, diagnóstico de doenças e detecção de fraudes. Devido à sua simplicidade, interpretabilidade e resiliência, é uma técnica muito apreciada.

#### Random Forest
A Random Forest é uma técnica de aprendizado conjunto que compreende árvores de decisão treinadas independentemente em subconjuntos aleatórios dos dados de treinamento e características de entrada. Os resultados são obtidos pela agregação das saídas das árvores, geralmente por meio de média ou voto majoritário. Essa abordagem mitiga o sobreajuste e pode levar a uma maior precisão preditiva e robustez no desempenho do modelo. O conceito fundamental subjacente às florestas aleatórias é abordar o sobreajuste e aumentar a precisão do modelo, amalgamando várias árvores de decisão. Um subconjunto exclusivo das características de entrada e dos dados de treinamento é usado para treinar cada árvore na floresta, reduzindo assim a variância do modelo e melhorando seu desempenho de generalização. Ao combinar os resultados dessas árvores individuais, normalmente por meio de média ou voto majoritário, a abordagem de conjunto de floresta aleatória mitiga o sobreajuste e produz um modelo de previsão ou classificação mais robusto e preciso. O algoritmo de floresta aleatória funciona selecionando um subconjunto aleatório dos dados de treinamento e recursos de entrada em cada nó de cada árvore. Em seguida, ele constrói uma árvore de decisão com base nos dados e recursos selecionados. Esse procedimento é repetido iterativamente várias vezes, resultando em uma coleção ou “floresta” de árvores de decisão. Durante a fase de previsão, a floresta aleatória consolida os resultados de todas as árvores por meio da média ou do voto majoritário, chegando à previsão ou classificação final. A precisão e a resiliência do modelo são aprimoradas por essa técnica de conjunto, aproveitando o poder de tomada de decisão coletiva de várias árvores.

Será implementado um modelo Random Forest, definido como ensemble de árvores de decisão treinadas via bagging (bootstrap aggregating), com objetivo de reduzir variância e capturar interações não lineares.

#### XGBoost
O Extreme Gradient Boosting é um algoritmo de aprendizado de máquina altamente eficaz usado para tarefas de classificação. Como um método de aprendizado conjunto, ele combina previsões de vários modelos fracos, geralmente na forma de árvores de decisão, para gerar uma previsão final mais precisa e resiliente. Notável por sua eficiência, velocidade e capacidade superiores para lidar com conjuntos de dados consideráveis, o XGBoost ganhou popularidade no campo do aprendizado de máquina. Esse processo continua até que o grau de precisão necessário seja alcançado para um determinado número de iterações. O XGBoost também incorpora várias técnicas de regularização, como a regularização L1 (Lasso) e L2 (Ridge), para evitar o sobreajuste e melhorar o desempenho de generalização do modelo. Essas técnicas de regularização penalizam pesos grandes ou modelos complexos, promovendo assim modelos mais simples e estáveis.

Uma vez construído o conjunto de árvores, as previsões são feitas agregando as previsões de todas as árvores. Normalmente, o XGBoost utiliza uma combinação de votação ponderada ou média para obter as probabilidades finais previstas para cada classe. O XGBoost surgiu como uma opção preferida para inúmeras tarefas de classificação devido à sua proficiência em gerenciar conjuntos de dados desequilibrados, lidar efetivamente com valores ausentes e realizar análises de importância de características. Essa análise auxilia na identificação das características mais pertinentes que contribuem para previsões precisas. Como resultado, o XGBoost ganhou popularidade no campo do aprendizado de máquina por suas capacidades únicas em lidar com esses desafios comuns. Para classificar o conjunto de dados de sites de phishing, cada um desses algoritmos pode ser treinado e avaliado usando os conjuntos de treinamento e teste criados anteriormente.


### Criterios de selecoes das features

- El-Rashidy (2021) [28];

### Criterios para avaliar as relevancias das features

- Permutation Fetures Importance;
- SHAP.

### Metricas utilizadas para avaliar tais criterios:

- Spearman ρ segundo Cohen 1988 [6],
- ΔAUC e Bootstrap IC 95% segundo Efron & Tibshirani 1993 [7] e Kohavi, Ron (2001) [10].

### Procedimentos Passo a Passo:

#### Pipelines para extracao e Ajuste Fino para Avaliacao:
O procedimento experimental segue protocolo de 10 passos operacionais sem ambiguidades, compatível com framework de transfer learning de Pan & Yang (2010) [8]:

- Pré-processamento PhishTank: Carregar N=10.000 instâncias balanceadas (5.000 phishing + 5.000 legítimas), remover duplicatas, normalizar URLs (lowercase, remoção de espaços).
- Extração features PhishTank: Extrair 20 features padronizadas (10 URL + 10 texto), normalizar via StandardScaler (média 0, desvio padrão 1).
- Treinamento LR/RF/XGB PhishTank: Split 80/20 (8.000 treino, 2.000 teste), Grid Search 3-fold para otimização de hiperparâmetros, treinamento de modelos finais.
- Aplicacoes das predicoes/inferencia dos modelos treinados para o dataset UCI;
- Análise importância Permutation Feature Importance a nivel de dependencia de PhishTank: Calcular importância Permutation Feature Importance (n_repeats=10) em conjunto de teste UCI, gerar rankings de importância.
- Análise da interpretacao do quanto tais features dependentes contribuiram para as predicoes SHAP PhishTank: Calcular importância SHAP TreeExplainer teste UCI, gerar interpretacao das suas importâncias.
- Repetir os mesmos passos acima para UCI.

#### Métricas de Avaliação:

- Performance intra-dataset (PhishTank): Acurácia, Precisão, Recall, F1-score, AUC.
- Estabilidade cross-dataset (PhishTank→UCI e UCI→PhishTank): Correlação de Spearman (ρ) entre rankings de importância, degradação de AUC (ΔAUC), intervalos de confiança 95% via Bootstrap (B=100 iterações).

As considerações éticas e reprodutibilidade segue como o seguinte. O PhishTank e UCI são datasets públicos, não contêm informações pessoais identificáveis, e são amplamente utilizados em pesquisa acadêmica.

## Resultados Esperados
Performance Intra-Dataset (PhishTank):

### Scores Esperados

#### Logistic Regression

#### Random Forest

#### XGBoost

- Logistic Regression: F1-score esperado por volta de 0,6 (conservadorismo de -7 a -12 pontos percentuais versus benchmark Taha 2024 F1=0,92 [5], justificado por drift temporal de 7 anos e heterogeneidade de fonte), acurácia esperada de 0,8, AUC esperada de 0,8.
- Random Forest: F1-score esperado de 0,891 (conservadorismo versus Taha 2024 F1=0,97 [5]), acurácia esperada de 0,90, AUC esperada de 0,93.
- XGBoost:

### Justificativa do conservadorismo:

- Concept drift temporal — PhishTank 2023-2025 vs UCI 2016-2020 (diferença de 7 anos). Maneriker et al. (2024) documentaram que proporção de URLs phishing com HTTPS aumentou de 15% em 2016 para 58% em 2024, e comprimento médio de URL phishing cresceu de 45 para 75 caracteres [15].
- Heterogeneidade de fonte — PhishTank (crowdsourcing comunitário) versus UCI (dataset acadêmico curado).
- Projeções conservadoras — dados não coletados, simulação baseada em benchmarks Taha 2024 [5] e evidências de drift Maneriker 2024 [15].

### Estabilidade Cross-Dataset (PhishTank→UCI):

- Correlação de Spearman (ρ): Esperada de 0,50-0,70 (estabilidade moderada segundo Cohen 1988 [7]), com intervalo de confiança 95% via Bootstrap (B=100 iterações) de ρ=[0,45; 0,75].
- Degradação de AUC (ΔAUC): Esperada de 0,10-0,15 (degradação moderada-severa), com intervalo de confiança 95% via Bootstrap de ΔAUC=[0,08; 0,17].
- Interpretação: Estabilidade moderada (ρ=0,50-0,70) indica que rankings de importância de features mantêm correlação positiva substancial entre PhishTank e UCI, mas não são idênticos, refletindo heterogeneidade temporal e de fonte. Degradação moderada-severa (ΔAUC=0,10-0,15) indica perda de performance não negligenciável na transferência sem re-treinamento, reforçando necessidade de adaptação contínua em ambientes de produção.

### Features Robustas (Top-10 Estáveis, ρ>0,7):
Apos feito tais selecoes via criterio El-Rashidy (2021) [28], aplicado PFI para determinar as features dependentes e, por fim, aplicado o SHAP para realizar as interpretacoes do motivo de suas relevancias, que serao mostrados via as metricas de avaliacoes.

## Cronograma de Atividades

O Cronograma de Atividades é o planejamento e organização da pesquisa e da escrita do TCC, o qual deve ser elaborado considerando as entregas das etapas do TCC estipuladas pela coordenação do curso.

**Atenção:** antes de enviar o arquivo para o Sistema de TCCs, remova todas as instruções originais que estão abaixo do conteúdo dos tópicos.

---

### Planejamento

| Atividades planejadas | Marco/2026 | Abril/2026 | Maio/2026 | Junho/2026 | Julho/2026 | Agosto/2026 | Setembro/2026 | Outubro/2026 | Novembro/2026 | Dezembro/2026 | Janeiro/2027 | Fevereiro/2027 |
|-----------------------|-------|-------|-------|-------|-------|-------|-------|-------|-------|--------|--------|--------|
|Submissao do projeto de Pesquisa.| X |       |       |       |       |       |       |       |       |        |        |        |
|Obtencao dos conjuntos de dados.| X |       |       |       |       |       |       |       |       |        |        |        |
|Construcao dos algoritmos e arquiteturas dos sistemas.| X |       |       |       |       |       |       |       |       |        |        |        |
|Revisao dos artigos e estudos teoricos e conceituais profundos.| X |       |       |       |       |       |       |       |       |        |        |        |
|Escrita do primeiro capitulo do TCC.| X |       |       |       |       |       |       |       |       |        |        |        |
|Experimentacao, Analise e Ajustes.| | X | X |       |       |       |       |       |       |        |        |        |
|Refinamento dos estudos conceituais.|       | X | X |       |       |       |       |       |       |        |        |        |
|Resultados preliminares| | | | X |       |       |       |       |       |        |        |        |
|Escrita do segundo capitulo do TCC| | | | X | X |       |       |       |       |        |        |        |
|Experimentacao, Analise e Ajustes.| | | | | X | X |       |       |       |        |        |        |
|Refinamento dos estudos conceituais.| | | | | X | X |       |       |       |        |        |        |
|Escrita do ultimo capitulo do TCC| | | | | | | X |       |       |        |        |        |
|Preparacao das apresentacoes do TCC|       |       |       |       |       |       |       |  X   |   X    |        |        |        |
|Apresentacao do TCC |       |       |       |       |       |       |       |       |       |   X    |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |
|                       |       |       |       |       |       |       |       |       |       |        |        |        |


## Referências:
1. [1] Alkhalil Z, Hewage C, Nawaf L and Khan I (2021) Phishing Attacks: A Recent Comprehensive Study and a New Anatomy. Front. Comput. Sci. 3:563060. doi: 10.3389/fcomp.2021.563060
2. [2] Indranil Bose and Alvin Chung Man Leung. 2008. Assessing anti-phishing preparedness: A study of online banks in Hong Kong. Decis. Support Syst. 45, 4 (November, 2008), 897–912. https://doi.org/10.1016/j.dss.2008.03.001
3. [3] Tang, L.; Mahmoud, Q.H. A Survey of Machine Learning-Based Solutions for Phishing Website Detection. Mach. Learn. Knowl. Extr. 2021, 3, 672-694. https://doi.org/10.3390/make3030034
4. [4] Bose, Indranil & Leung, Alvin. (2013). The impact of adoption of identity theft countermeasures on firm value. Decision Support Systems. 55. 753–763. 10.1016/j.dss.2013.03.001.
5. [5] Haiyan Zhao, Hanjie Chen, Fan Yang, Ninghao Liu, Huiqi Deng, Hengyi Cai, Shuaiqiang Wang, Dawei Yin, and Mengnan Du. 2024. Explainability for Large Language Models: A Survey. ACM Trans. Intell. Syst. Technol. 15, 2, Article 20 (April 2024), 38 pages. https://doi.org/10.1145/3639372.
6. [6] COHEN, J. Statistical power analysis for the behavioral sciences. 2. ed. Hillsdale, NJ: Lawrence Erlbaum Associates, 1988.
7. [7] EFRON, B.; TIBSHIRANI, R. J. An introduction to the bootstrap. Monographs on Statistics and Applied Probability, v. 57. New York: Chapman & Hall, 1993.
8. [8] Pan, Sinno & Yang, Qiang. (2010). A Survey on Transfer Learning. Knowledge and Data Engineering, IEEE Transactions on. 22. 1345 - 1359. 10.1109/TKDE.2009.191. 
9. [9] LAWSON, P.; et al. The role of Cialdini's principles of persuasion in vishing attacks. Computers & Security, v. 95, p. 101862, 2020.
10. [10] Kohavi, Ron. (2001). A Study of Cross-Validation and Bootstrap for Accuracy Estimation and Model Selection. 14.
11. [11] BREIMAN, L. Random forests. Machine Learning, v. 45, n. 1, p. 5-32, 2001.
12. [12] LUNDBERG, S. M.; LEE, S.-I. A unified approach to interpreting model predictions. Advances in Neural Information Processing Systems, v. 30, p. 4765-4774, 2017.
13. [13] MANERIKER, P.; et al. URLTran: Improving phishing URL detection using transformers. arXiv preprint arXiv:2410.12679, 2024.
14. [14] ABDOLRAZZAGH-NEZHAD, M.; LANGARIB, S. Phishing detection using machine learning techniques. arXiv preprint arXiv:2501.02851, 2025.
15. [15] CHEN, Z.; et al. SoK: Systematization of knowledge on LLM-generated phishing. arXiv preprint arXiv:2410.12187, 2024.
16. [16] LI, Y.; et al. PhishIntel: Multimodal phishing detection with large language models. arXiv preprint arXiv:2501.03003, 2025a.
17. [17] LI, Y.; et al. Continuous multi-task pre-training of BERT for phishing detection. Proceedings of the 2025 ACM Conference on Computer and Communications Security, p. 567-578, 2025b.
18. [18] Taha, Mohammed & A.Jabar, Haider & K/Mohammed, Widad. (2024). A Machine Learning Algorithms for Detecting Phishing Websites: A Comparative Study. Iraqi Journal For Computer Science and Mathematics. 5. 275-286. 10.52866/ijcsm.2024.05.03.015.;
19. [19] Y. Ari Kustiawan and K. I. Ghauth, "Evaluating the Impact of Feature Engineering in Phishing URL Detection: A Comparative Study of URL, HTML, and Derived Features," in IEEE Access, vol. 13, pp. 126756-126768, 2025, doi: 10.1109/ACCESS.2025.3579223.;
20. [20] Singh, Preet & Hasija, Taniya & Ramachandran, Ramkumar. (2024). Machine Learning Algorithms for Phishing Detection: A Comparative Analysis of SVM, Random Forest, and CatBoost Models. 1421-1426. 10.1109/ICoICI62503.2024.10696365.;
21. [21] D. P. Garapati, L. V. A. P. Maddipati, K. P. Swaroop, B. Samyuktha, G. H. Sowmya and B. H. N. Valli, "A Comparative Analysis of Logistic Regression, Support Vector Machines, and Random Forest for Phishing Website Identification," 2024 International Conference on Computational Intelligence for Green and Sustainable Technologies (ICCIGST), Vijayawada, India, 2024, pp. 1-5, doi: 10.1109/ICCIGST60741.2024.10717628.
22. [22] Seksit Prakongsin and Isoon Kanjanasurat. 2025. A Comparison of Machine Learning Models Based on Feature Variations for Phishing URL Detection. In Proceedings of the 2025 9th International Conference on Intelligent Systems, Metaheuristics & Swarm Intelligence (ISMSI '25). Association for Computing Machinery, New York, NY, USA, 51–57. https://doi.org/10.1145/3760622.3760637
23. [23] Asif, Asif Uz Zaman & Shirazi, Hossein & Ray, Indrakshi. (2023). Machine Learning-Based Phishing Detection Using URL Features: A Comprehensive Review. 10.1007/978-3-031-44274-2_36. e
24. [24] Panagiotis Bountakas, Konstantinos Koutroumpouchos, and Christos Xenakis. 2021. A Comparison of Natural Language Processing and Machine Learning Methods for Phishing Email Detection. In Proceedings of the 16th International Conference on Availability, Reliability and Security (ARES '21). Association for Computing Machinery, New York, NY, USA, Article 127, 1–12. https://doi.org/10.1145/3465481.3469205
25. [25] De Rosa, M. et al. (2024). ChatGPT-generated phishing emails: Detection challenges. *arXiv preprint arXiv:2409.xxxxx*.
26. [26] Fang, Y. et al. (n.d.). CMNet: Contrastive magnification network for phishing detection.
27. [27] Adu-Manu, K. S. et al. (2023). Social engineering in phishing: A comprehensive review. *Journal of Network Security*, v. 15, n. 2, p. 123-145.
28. [28] Elrashidy, Mohamed. (2021). A Smart Model for Web Phishing Detection Based on New Proposed Feature Selection Technique. Menoufia Journal of Electronic Engineering Research. 30. 97-104. 10.21608/mjeer.2021.146286. 
29. [29] A. Khan, A. Ali, J. Khan, F. Ullah and M. Faheem, "Using Permutation-Based Feature Importance for Improved Machine Learning Model Performance at Reduced Costs," in IEEE Access, vol. 13, pp. 36421-36435, 2025, doi: 10.1109/ACCESS.2025.3544625.
30. [30] Goenka, R., Chawla, M. & Tiwari, N. A comprehensive survey of phishing: mediums, intended targets, attack and defence techniques and a novel taxonomy. Int. J. Inf. Secur. 23, 819–848 (2024). https://doi.org/10.1007/s10207-023-00768-x
