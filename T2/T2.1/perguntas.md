Minha ideia original era explorar o repositorio do kernel do linux no github e trabalhar mais nos contribuidores e suas informacoes e contribuicoes. 
Meu plano era me aproveitar do formato de mensagem do commit para criar tags como 'documentacao', 'fix', etc 
Porem encontrei 3 problemas nisso:
* O numero de commits e contribuidores eh mto grande. O que torna tudo mais lento.Nao foi um grande problema, mas foi bem acima do que eu esperava. o github faz rate limiting de requests mas convenientemente tambem da o timestamp de quando seu rate reseta, entao com um cron basico driblei isso. utilizei o PyGithub.
* Mensagens de commit, usuarios e etc nao sao padronizados. Recentemente existe um padrao, mas este padrao foi mudando e nao eh 100% respeitado. Alem disso, mesmas pessoas commitam usando emails e nomes diferentes ao mesmo tempo que uma parte significativa dos contribuidores (acima de 50%) nao possuem conta no github.
* Mudanca em nomes de arquivos e padroes ao longo dos anos, sem momentos de centralizacao (de onde eu poderia comecar a contar). Fazendo com que o tracking de arquivos ficasse bem mais dificil.

Resolvi entao fazer analises mais cruas e menos focadas nas pessoas.

descricao do dataset:

> timestamp message [file]

cada linha representa um commit com seu timestamp, sua mensagem e arquivos afetados. cada arquivo tem a seguinte estrutura:

> name format add rem change

nome, formato (extensao: '.c','.h'), adicoes, remocoes e mudancas (ints)

em termos de numpy, o dataset tem shape (N,1,5) 
 

Dividi as questoes em 3 grupos: inferencia direta, classificacao (regressao logistica) e inferencia complexa.
No primeiro grupo, busco prever dados a partir de dados brutos. Por exemplo, ao gerar strings, o metodo utilizado olhara apenas como um vetor de chars. Mesmo assim, acho que posso encontrar resultados interessantes.
No segundo, vou tentar classificar usando a mensagem, como descrito acima, porem sabendo que nao terei sucesso, tentarei classificar o resto baseado na classificacao parcial. 
No terceiro, tentarei atingir algo parecido com o primeiro grupo porem com metodos mais 'semanticos' como lstm, charnn ou o word2vec. Vou colocar isso como 'ponto-extra' no sentido que pode demandar muito poder computacional.

Em todos os casos, utilizarei o scikit learn (tirando o ultimo).

inferencia direta:

	inferir proximo commit (inferindo o timestamp) sabendo a historia
		inferir proximo timestamp
		inferir proxima mensagem
		inferir proximos arquivos
		existe diferenca se considerarmos estas variaveis independentes ou dependentes? (em um inferimos 3 coisas e juntamos, no outro inferimos 1 coisa)
	inferir commit sabendo a mensagem
		arquivos e timestamp
		colocando um determinado termo, o commit eh gerado no passado ou no futuro? 
		sera que geraremos commits em arquivos antes deles serem criados?
	inferir commit sabendo o timestamp
		mensagem e arquivos
		como seria um commit artificial no ponto X do projeto? 
		e daqui a N anos?
		e antes do projeto comecar?
	inferir commit sabendo extensoes
		mensagem, add/rem/change e timestamp
		sera que conseguimos seguir o padrao de commit do linux?
	inferir commit sabendo X
		seria legal um metodo generico 
			gen_commit.where(extension='.c',timestamp=1234)

regressao logistica:

	classificar em documentacao, feature e bugfix
	
	adicionando a coluna tipo, 
		repetir as inferencias sabendo este novo dado

regressao complexa

	usar charnn (ele usa no codigo do linux no fim)
		http://karpathy.github.io/2015/05/21/rnn-effectiveness/
		https://hub.docker.com/r/mbartoli/char-rnn/
	usar word2vec
	~usar ferramentas de nlp~ na verdade eu desisti disso
	usar rede neural end2end (commit->commit) sem memoria
	usar rede neural end2end (commit->commit) com memoria (lstm)
	pensei em colocar markov tambem mas acho redundante, se der tempo posso tentar usar boltzman ou hmm
	

Consideracoes:
	commits representam transicoes de estados.
	estarei buscando funcoes que estimam transicoes de estados sem nunca olhar os estados-em-si.
	acredito que nao aparecerao resultados muito interessantes.
	Depois seria interessante atualizar estes metodos para um modelo contextual (nao no sentido dos ultimos X commits) mas nos sentidos (commit,estado da codebase) e historia (commit->codebase->commit->codebase).
	Sempre olhando um branch.
	Uma analise em muitos branches ja seria topico de um outro trabalho.(ainda mais se considerarmos variacoes de topologia)
