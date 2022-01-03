<h3 align="center">Utilizando o Cypress E2E para testar um Blog em Angular</h3>

<p align="center">
  <img src="./assets/dio.png" alt="DIO" title="Digital Innovation One">
</p>


Neste projeto você terá o desafio de construir um teste E2E com Cypress para um Blog em Angular.

# Utilizando o Cypress E2E para testar um Blog em Angular 

- Cypress é uma ferramenta web
- Você não precisa programar todos os testes 
- executa em um navegador 
- nao automatiza todos os testes 
- aplicativo real-world example 

- git clone https://github.com/gothinkster/angular-realworld-example-app.git
- npm i 

-- dev só serve para desenvolvimento 

- npm install cypress --save-dev

- npx cypress -v 

- npm uninstall --save-dev protrector 
- deletamos o diretorio e2e
- do package.json remover o e2e : nge2e 
- npx cypress open

#  Como funciona

No momento, estamos trabalhando em alguns documentos para a base de código (explicando onde a funcionalidade está localizada, como funciona, etc), mas a base de código deve ser simples de seguir como está. Também lançamos um [ tutorial passo a passo com screencasts ] (https://thinkster.io/tutorials/building-real-world-angular-2-apps) que ensina como recriar a base de código do zero .

###  Fazendo solicitações para a API de back-end

Por conveniência, temos um servidor de API em execução em https://conduit.productionready.io/api para o aplicativo fazer solicitações. Você pode ver [ as especificações da API aqui ] (https://github.com/GoThinkster/productionready/blob/master/api) que contém todas as rotas e respostas para o servidor.

O código-fonte do servidor backend (disponível para Node, Rails e Django) pode ser encontrado no [ repositório principal RealWorld ] (https://github.com/gothinkster/realworld).

Se você quiser alterar a URL da API para um servidor local, simplesmente edite `src / environment / environment.ts` e altere` api_url` para a URL do servidor local (ou seja, `localhost: 3000 / api` )


#  Primeiros passos

Certifique-se de ter o [ Angular CLI ] (https://github.com/angular/angular-cli#installation) instalado globalmente. Usamos [ Yarn ] (https://yarnpkg.com) para gerenciar as dependências, por isso é altamente recomendável que você use. você pode instalá-lo [ aqui ] (https://yarnpkg.com/en/docs/install) e, em seguida, executar `yarn install` para resolver todas as dependências (pode demorar um minuto).

Execute `ng serve` para um servidor de desenvolvimento. Navegue até `http: // localhost: 4200 /` . O aplicativo será recarregado automaticamente se você alterar qualquer um dos arquivos de origem.

###  Construindo o projeto
Execute `ng build` para construir o projeto. Os artefatos de construção serão armazenados no diretório `dist /` . Use o sinalizador `-prod` para uma construção de produção.


##  Visão geral da funcionalidade

O aplicativo de exemplo é um site de blog social (ou seja, um clone do Medium.com) chamado "Conduit". Ele usa uma API personalizada para todas as solicitações, incluindo autenticação. Você pode ver uma demonstração ao vivo em https://angular.realworld.io

** Funcionalidade geral: **

- Autenticar usuários via JWT (páginas de login / inscrição + botão de logout na página de configurações)
- Usuários CRU * (página de inscrição e configurações - sem necessidade de exclusão)
- Artigos CRUD
- CR * D Comentários sobre os artigos (sem necessidade de atualização)
- OBTER e exibir listas paginadas de artigos
- Artigos favoritos
- Siga outros usuários

** A divisão geral da página é assim: **

- Página inicial (URL: / # /)
    - Lista de tags
    - Lista de artigos obtidos de Feed, Global ou por Tag
    - Paginação para lista de artigos
- Páginas de login / inscrição (URL: / # / login, / # / registrar)
    - Usa JWT (armazena o token em localStorage)
    - A autenticação pode ser facilmente alternada para baseada em sessão / cookie
- Página de configurações (URL: / # / settings)
- Página do editor para criar / editar artigos (URL: / # / editor, / # / editor / article-slug-here)
- Página do artigo (URL: / # / article / article-slug-here)
    - Botão Excluir artigo (mostrado apenas para o autor do artigo)
    - Renderizar a redução do lado do cliente servidor
    - Seção de comentários na parte inferior da página
    - Botão Excluir comentário (mostrado apenas para o autor do comentário)
- Página de perfil (URL: / # / perfil /: nome de usuário, / # / perfil /: nome de usuário / favoritos)
    - Mostrar informações básicas do usuário
    - Lista de artigos preenchida a partir de artigos criados pelo autor ou artigos favoritos do autor
