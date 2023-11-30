## Introdução
1. Uso da internet em conexões  um para um e um para todos, ou todos para todos.
2. Uso de detecção de comunidade, previsão de links , ou seja para onde uma link leva.
3. Identificar pessoas com comportamento criminoso.
________
## Problema em si
* Uso da redes sociais para que grupo voltado a pedofilia, terrorismo, dentre outro, sejam identificados e punidos
* Identificar pessoas suspeitas é muito complicado, ao menos usando aprendizando de máquina, pois a mudança de palavra e e seus significados muda muito de grupo para grupo, dificultando o aprendizado de máquina de algo como os jargões utilizados por um grupo.
______________________________________________________
## Problemas de Pequisas Específico 
* Uso de abordagem não supervisionada.
* Ponderar os termos por meio de recurso semântico
___
## Questões da Pesquisa
* Como evitar termos frequentes de serem impecílios na identificação de criminosos*
* Como identificar os criminosos por meio de interações implícitas.
* Quais métricas topológicas conhecidas ou adaptadas na literatura podem auxiliar a identificação de pessoas suspeitas sem estarem atreladas a um domínio específico.
___
## Metodologia
* Análise de mensagens e interações nas redes sociais 
* Análise de redes sociais, descoberta e representação do conhecimento*
* Uso do método Inspection -> Abordagem não supervisionada. Método é utilizado para verificar se a interação é implícita ou explícita.
___
## Fundamentação Teórica

### Análise de Redes Sociais 
Considerando os diferentes contextos em que os indivíduos em uma rede se encontram(socioeconômicos, político, religioso, etc ...). Para a análise do projeto, foram utilizados multigrafos, com o intuito de analisar os indivíduos e suas relações. As análises topológicas e contextuais serão feita em cima dessas relações. 

(Dar exemplo de imagens com grafos)

* **Informação Topológica***: Busca ter um entendimento melhor sobre as conexões existentes por meio de métricas, as quais permitem o cálculo e quantificação das diferentes interpretações desses indivíduos. Algumas das métricas citadas no trabalho e comum no tópico de grafos são
	* _Grau do Vértice:_ Permite saber o número de conexões que um indivíduo possui com o outro.
	* _Reputação_: Verifica a importância de um indivíduo dentro da rede em grafos dirigido.
	* _Centralidade de Intermediação_: Cálculo de número de vezes que um vértice serve como caminho para outros vértices. ou seja, mede a capacidade de um vértice de conectar outros vértices a vértices importantes.
* **Informação Contextual**: Em contexto de rede social, corresponde a dados não estruturados, como mensagens, comentários e publicações.
* **Abordagem Supervisionada**: Usa dados previamente rotulados, os rótulos desses dados são utilizados como parte do subconjunto de  "Treino" , utilizado em algoritmos de aprendizado de máquina, "Teste", utiliza o modelo gerado pelo aprendizado de máquina para testar a validade dos dados por métricas de avaliação .
* **Abordagem  Não-Supervisionada**: diferentemente da Abordagem Supervisionada, não existe a necessidade de se ter um conjunto de dados previamente rotulado, por exemplo, na tarefa de identificação de pessoas suspeitas de crimes em redes sociais, não existe a necessidade de se ter rotulado quem é ou não suspeito. Em seguida, uma ou mais dessas informações são utilizadas ou mescladas a fim de ser gerado um score que demonstre numericamente

### Descoberta de Conhecimento em Texto
a informação precisa ser concreta e com erros minimizados ao máximo, com o intuito de garantir os ganhos ao assumir uma determinada estratégia. Nesse contexto, existe a Descoberta de Conhecimento que busca extrair informações úteis de maneira automatizada e conhecimentos por meio da manipulação e análise de
um grande volume de dados.
#### Pré-Processamento
a etapa de pré-processamento busca realizar uma limpeza nos dados textuais a fim de capturar a verdadeira essência do texto, reduzir o esforço computacional e verificar as palavras e frases que serão consideradas nas próximas etapas. A etapa de pré-processamento é composta por tarefas que permitem.

* **Tokenização**: Dado um texto, essa tarefa busca separá-lo em tokens. Exemplificando,considerando a frase “vc vai à praia!”, ao realizar a tokenização dela, se obtém os tokens: [vc], [vai], [à], [praia], [!]. A partir desses tokens, outras subtarefas são empregadas a fim de tratar possíveis ruídos que eles (e.g. abreviações, emotions, entre outros) podem possuir. Ex; – Abreviações e Siglas, Palavras Combinadas, Case Folding, Emotions.
* **Stemização**: É o processo de remoção de flexões linguísticas para identificar a raiz de uma palavra. Exemplificando, considerando as palavras “química”, “químicas”, “químico” e “químicos” a realizar a stemização dessas palavras, todas seriam “químic”. É válido informar que de acordo a stemização não é aplicável a todos os idiomas, por exemplo, no chinês que utiliza logogramas.
* **Remoção de Stop Word**: Stop Words são palavras irrelevantes, as quais comumente são usadas para juntar palavras em um frase (e.g.e, são, isto, etc.).Essas palavras são caracterizadas por serem altamente frequentes. Dessa forma, considerá-las geraria um esforço computacional desnecessário.
* **Vetorização:** A vetorização é uma das principais tarefas na etapa de pré-processamento, por meio dela busca-se realizar a conversão de um conteúdo textual em representações numéricas para que possam ser compreendidas por máquinas. Existem diversas métricas e métodos para realização dessa conversão, porém a mais utilizada é a TF-IDF., captura a importância semântica de uma palavra em um documento específico d, rebaixando palavras que tendem a aparecer em corpus com N documentos.
## Método Inspection
Através das informações topológicas e contextuais recolhidas, extraídas a partir das interações implicitas e explicitas entre as pessoas por meio das suas trocas de mensagens e de seus conteudos textuais, serão identificados os suspeitos de crimes.

![[recorteDaRede.png]]

1. **Recorte da Rede**:Nesta etapa, dado um conjunto de dados N composto por interações ocorridas em uma rede social, busca-se construir um conjunto de mensagens M enviadas ou recebidas por pessoas de um conjunto U , cada mensagem m x é um conjunto ordenado de termos.
	![[recorteDaRede 1.png]]

	1. **Algoritmo TROY**: Utilizado para explicitar interações mais implicitas, como comentários em plataformas de vídeo como o youtube. Portanto dado um recorte de uma rede, essa é representada por conjuntos de comentários, pessoas e respostas, sendo que cada comentário está sempre ligada a uma resposta, e cada pessoa pode estar em um comentário, uma resposta ou ambos. Os comentários e respostas podem ser divididos nas seguintes categorias:

		* **Comentário Impactante(CI)***: Ocorre quando é respondido por ao menos uma pessoa.
		* **Comentário não Impactante(CNI)**: Ocorre quando não é respondido, esses comentários não são considerados pelo algoritmo TROY, pois nenhuma pessoa foi impactada, devido à ausência de respostas.
		* **Resposta Direta(RD)**: Não há citação de uma pessoa, apenas a afirmação de que algo acontecerá(ex: Irei Viajar!).
		* **Resposta Direta e Indireta(RDI)**: Uma pessoa responde um comentário impactante mencionando outra pessoa que o respondeu previamente.
 
		 Como entrada o algoritmo recebe um conjunto de pessoas, comentários e respostas e retorna um conjunto de pessoas que realizaram interações e um conjunto M com as mensagens envolvidas pertencentes ao conjunto de pessoas. O funcionamento do algoritmo se dá em duas fases F1 e F2. em F1 são identificadas as trocas de mensagens do tipo CI, RD e RDI, ussando o conjunto de RDI para identificar as respostas que tiveram citações direcionadas ao responsável pelo comentário. a parte F2 é utilizada para identificar as interações entre as pessoas por meio das respostas.![[algoritmoTROY.png]]

2. **Preparação dos Termos**: O conjunto de mensagens obtido é tratado afim de se obter apenas os termos normalizados e padronizados mais relevantes a serem analisados. Esta etapa segue algumas etapas.
		1. **Normalização e Extração de Dados Textuais**: trata cada termo de uma mensagem do conjunto de mensagens para remover certos ruidos como letras repetidas, pontuações, sinais, acentos, gírias, abreviações, entre outros ruídos.
		2. **Remoção de _Stop Word_**: trata cada palavra que não demonstram comportamento. retirando-as do conjunto de mensagens.
		3. **Stemização**: retira o radical das mensagens para identificar a raiz de suas palavras.
		 
			![[preparacaoDosTermos2.png]]
	
3. **Representação da Rede**: O novo conjunto de mensagens aliado ao conjunto de pessoas previamente conhecidos, permite a construção de multígrafos que representem as conexões entre as pessoas e as suas mensagens.
         ![[representacaoDaRede.png]]
	 * **Pessoa-Pessoa***: Multigrafo dirigido, os vértices as pessoas envolvidas em uma interação em que.
		  ![[multigrafoPessoaPessoa.png]]
	* **Pessoa-Mensagem-Pessoa**: Multigrafo dirigido, os vértices representam tanto as pessoas quanto os termos direcionados a elas.*
		  ![[multigrafoPessoaTermoPessoa.png]]

4. **Ponderação do Vocabulário Controlado**: Para esta etapa deve-se ter em foco o domínio que se deseja explorar. no caso do presente trabalho, a pedofilia. Para montar o vocabulário ponderado, seguem as seguintes etapas:
	 ![[ponderaçãDosTermos.png]]
	
	1. **Classes e subclasses**: Por meio de um multigrafo são representadas as ligações entre os termos até que se chegue ao domínio que se explora. Sendo as classes o segundo nível da árvore n-ária e os outros níveis como subclasses da árvore, para cada classe temos um peso atribuido à sua importância.
	 	![[classesSubclasses.png]]	 
	2. **Identificação do conjunto de termos suspeitos**: É construido um conjunto novo a partir da intersecção entre os termos que são subclasses e todos os termos extraídos da etapa de representação de rede, incluindo os nomes dos usuários.
		 ![[conjuntoDeTermosSuspeitos.png]]
	3. **Peso Global**: Para cada termo pertencente ao novo conjunto criado, é feito uma medida de importância baseada no quanto cada termo não aparece. O seu calculo consiste no log de base dois da razão entre o número de arestas totais do conjunto multigrafo pessoa-pessoa e os termos do conjunto A.
		 ![[pesoGlobal.png]]
	4.  **Peso global máximo**: Peso global máximo que um termo pode ter. log na base 2 do   total de arestas que possui os termos do conjunto A.
		 ![[pesoGlobalMáximo.png]]
		 Em seguida é tirado o peso máximo para cada elemento em A.
		 ![[pesoGlobalMáximoc.png]]
	5. **Peso Global Normalizado**:  Definido a partir 


5. **Análise da Rede**: Análise das informações contextuais e topológicas a partir do recorte da rede.