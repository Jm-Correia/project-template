## Typescript:
> ### Motivação:
>  Minha maior motivação pelo uso do typescript foi pelo fato de facilitar demais o meu entendimento e me ajudar a ser mais produtivo. Eu ainda programo em Java e quando comecei a estudar e participar de alguns projetos a transição foi bem difícil pois o NodeJS possui certos aspectos que um dev Java, um tanto antigo kkk, não estava acostumado.
>
> Atualmente no dia a dia de um projeto notei o quanto foi assertivo introduzir o typescript e quanto foi "mais" fácil para o time se adequar ao uso.

## Configurações, Debug e Deploy:

> ### **Instalação:**
> Para realizar a instalação rodamos o comando:
>```sh
> $ yarn add typescript -D
>```
> Após ter instalado precisamos configurar e gerar o *tsconfig.json* que é o arquivo responsável por ter as configurações do projeto.
> Executamos:
>```sh
> $ yarn tsc --init
>```
> Vemos que o arquivo foi gerado no explorer do projeto.
> Aqui vou deixar o link do site oficial explicando o que é cada coisa dentro deste arquivo. [What is tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
> Caso você queria dar um olhada no meu arquivo é só clicar aqui: [tsconfig.json](../tsconfig.json)

> ### **Ambiente de desenvolvimento:**
> Para ambiente de desenvolvimento temos que realizar a escolha de automatizar e melhorar nossa produtividade utilizando alguma biblioteca que nos ajude a reconhecer que o código sofreu alguma mudança e reiniciar o servidor para testarmos.
>
> Assim que iniciei meus estudos com NodeJS em 2018 fui direcionado a utilizar o *nodemon* ferramenta incrível que me ajudou muito. Muito utilizada para ambientes javascript e logo pesquisando mais encontrei outras como Sucrase e ts-node-dev.
>
>Aqui segue um link do pessoal da [rocketseat](https://blog.rocketseat.com.br/ferramentas-de-compilacao-execucao-em-tempo-de-desenvolvimento-dos-projetos-em-node-js/) que explica a diferença das 3 ferramentas dando uma breve visão de quando utilizar cada uma.
> Desde que comecei a usar *typescript* optei por utilizar **ts-node-dev** mesmo para aqueles projetos que não uso "Decorators".
>
> *No link mencionado da rocketseat tem a explicação de como instalar e configurar.*

> ### **Mapeando os Paths do projeto:**
> Para certos projetos onde a estrutura de pastas e os níveis são mais densos minha experiência com esta biblioteca ajudou o time a entender melhor a estrutura e até ser mais produtivo.
> Biblioteca: **tsconfig-paths**
>
> Ela lida com a importação de arquivos em tempo de desenvolvimento e lá no "deploy" do seu projeto para produção podemos resolver todas as importações sem maiores problemas.
>
> Devemos instalar usando:
>```sh
> $ yarn add tsconfig-paths -D
>```
> Aqui neste ponto precisamos alterar nosso arquivo de configuração *tsconfig.json* e criar os paths que desejamos ter.
>
> PS -> Eu não crio paths para tudo, apenas para os mais utilizados ou para quando o nível hierárquico for muito denso.
> Exemplo:
>```json
>{
>  "compilersOptions": {
>    "baseUrl": ".",
>    "paths": {
>      "@controllers/*": ["./src/>controllers/*"],
>      "@models/*": ["./src/models/*"],
>      "@config/*": ["./src/config/*"],
>      "@utils/*": ["./src/utils/*"]
>    }
>  }
>}
>```
> Após isso podemos importar da seguinte forma:
~~~javascript
import {User} from '@models/users/User'
~~~
> em nosso package.json no script dev precisamos registrar a utilização da lib da seguinte forma:
>```json
> "scripts": {
>    "dev": "ts-node-dev -r tsconfig-paths/register src/server.ts"
>  },
>```

> ### Debug:
>

