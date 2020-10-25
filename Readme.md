# Template Projetos

## Padronização de Código
> A ideia de padronizar o código é super importante pois é um dos grandes desafios de se trabalhar em time é o padrão que cada dev utiliza. Como sabemos, o código é um artefato vivo e cada desenvolver programa de uma forma diferente tendo cada um os seus costumes ou até aquele seu editor preferido.
>
> Imaginemos o caos de cada trecho, ou arquivo ficando de uma jeito diferente. Ex: ponto e virgula no fim ou não, aspas duplas ou não...
>
> Quem olhar o projeto de fora sentirá uma confusão mental e uma grande dificuldade de entender.
>
> Como dev devemos sim pensar na padronização do nosso código para que ele se torna mais legível. Indo além temos o "dever" de padronizar nosso código para que quando os outros desenvolvedores precisem: criar, salvar e "comitar" uma nova mudança tudo esteja padronizado de acordo com as definições iniciais do projeto.
>
> No final indicarei alguns extensões muito uteis que acredito que nós devs precisamos utilizar e explicarei o motivo de cada uma. [clique aqui](#extensoes) caso queria ir direto para o trecho.

### Ferramentas para padronizar este projeto:

> [EditorConfig](#editorconfig)
>
> [ESLint](#eslint)
>
> [Prettier](#prettier)

Abaixo segue as configurações, de cada ferramenta, que utilizei para este projeto, seguirei na ordem acima.

#### <a id="editorconfig">[EditorConfig](https://editorconfig.org/): </a>
> Esta ferramente nos auxilia na padronização das configurações quando os integrantes do time tem preferência por IDE`s diferentes.
>
> - Primeira coisa:
>
> 1. Instalamos a extensão no VSCode chamada ["EditorConfig for VS Code"](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig).
> 2. Após instalada, clicamos com o botão direito no explorer do projeto e selecionamos **Generate .editorconfig** .
> 3. Com o Arquivo **.editorConfig** gerado podemos definir o padrão desejamos.
> Para este projeto define da seguinte forma:
> ``` JAVASCRIPT
>root = true
> [*]
> indent_style = space
>indent_size = 4
>charset = utf-8
>trim_trailing_whitespace = true
>insert_final_newline = true
>end_of_line = lf
> ```
> - O que padronizamos aqui?
> 1. Inserimos uma nova linha no final.
> 2. Padronizamos a quebra de linha entre Sistemas Operacionais.
> 3. Removemos os espaços em branco de novas linhas.

#### <a id="eslint">[Eslint](https://eslint.org/docs/rules/)</a>
> Esta sem dúvidas é uma ferramenta poderosa que nós auxilia a padronizar o código podendo ser utilizado para projetos NodeJS, ReactJS, ReactNative entre outros.
>
> Sabemos que no javascript alguns pontos são *facultativos* por exemplo: o uso do *Ponto-Virgula*, tanto faz *aspas duplas* ou *simples* e por vai.
> Neste ponto tanto a definição de como organizar nossa estrutura interna (*diretórios*) quanto ao código deixará todo o time mais produtivo e de quebra o cliente satisfeito saner que todos seguem um padrão e por ser tranquilo de testar e analisar o código de forma estática.
>
> - Primeira coisa:
>
> 1. Instalamos a extensão no VSCode chamada ["ESLint"](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).
> 2. Uma coisa que muitos desenvolvedores esquecem é configurar seu vsCode "settings" para que quando ao salvar o arquivo as regras definidas sejam aplicadas.
> É so abrir o settings do vsCode:
>```
> ctrl + shift + p
>```
> Selecionar *Open Settings (JSON)* e adicionar o trecho abaixo:
>``` JSON
> "editor.codeActionsOnSave": {
>   "source.fixAll.eslint": true
> }
>```
> *Caso não funcione devemos dar um reload no vsCode.*
>
> 3. Vamos instalar o Eslint como uma dependência de desenvolvimento dentro do nosso projeto.a:
> ``` sh
> $ yarn add eslint@6.8.0 -D
> ```
> *Pelo fato da verão 7 está apresentando alguns erros optei por esta acima.*
> 4. Iremos iniciar o eslint no projeto:
>``` sh
> $ yarn eslint --init
>```
> 5. Será feito uma serie de perguntas onde devemos responder de acordo com o uso e desenho do projeto. Abaixo segue as que foram respondidas para este projeto:
>       1. To check syntax, find problems and enforce code style
>       2. Javascript modules (import/export)
>       3. None of these
>       4. YES
>       5. Utilizando a barra de espaço desmarcamos o Browser e Marcamos o __NODE__
>       6. Use a popular style guide
>       7. Airbnb
>       8. JSON
>       9. Por ele pergunta se queremos instalar as dependências listadas como estou utilizando o yarn opto por NO.
>       10. Copiamos o comando e rodamos utilizando *Yarn*:
>```sh
> $ yarn add @typescript-eslint/eslint-plugin@latest eslint-config-airbnb-base@latest eslint-plugin-import@^2.21.2 @typescript-eslint/parser@latest -D
>```
> 6. Criamos o arquivo *.eslintignore*.
> 7. E por fim devemos configurar o arquivo *.eslintrc.json*. Neste momento eu tenho uma cola para preencher. Para dúvidas veja a pagina principal do Eslint.
> 8. Adicionamos a lib:
>```sh
> $ yarn add eslint-import-resolver-typescript -D
>```
#### <a id="prettier">[Prettier](https://prettier.io/docs/en/options.html)</a>
> Esta ferramenta nos ajuda a estilização do nosso código. Ex: não permitir que uma linha seja maior que 100 caracteres, adicionar *Ponto-virgula* entre outras.
> - Antes de tudo:
>
> *Caso tenhamos instalado a extensão *Prettier* devemos remover ou desabilitar o uso para não termos conflito com este projeto em questão.
> - Vamos lá:
>
> 1. Vamos adicionar ao projeto as seguintes bibliotecas:
> ```sh
> $ yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
>```
> 2. Adicionamos ao *.eslintrc.json* o seguinte trecho:
>```json
>{
>	...
>  "extends": [
>		...
>    "prettier/@typescript-eslint",
>    "plugin:prettier/recommended"
>  ],
>  ...
>  "plugins": [
>    ...
>    "prettier"
>  ],
>  "rules": {
>    ...
>		"prettier/prettier": "error"
>  },
>  ...
>}
>```
> 3. E por fim criamos o arquivo *prettier.config.js* para resolvermos os conflitos entre *ESLint* e *Prettier*.
>
