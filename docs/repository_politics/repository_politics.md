# Políticas de Repositório de código
## Política de Commits
Adota-se para este projeto padrões para o comentário e execução dos commits. O idioma padrão para efetuar commits neste repositório é o inglês. As mensagens devem ser sucintas e expressarem de forma clara e objetiva a ação do commit.

Como exemplo, considere o trabalho da construção de uma tela inicial da aplicação. O commit deverá ser efetuado como segue:
```
git commit -m "Create new home Screen"
```

Atente ainda para os seguintes aspectos:
* O commit deve iniciar com letras maiúsculas.
* O commit deve iniciar com verbo no infinitivo.
Exemplos:  
-"Fix login auth error"  
-"Create User model"  
-"Refactor profile View"  
-"Translate flat pages"

## Política de Branches
O repositório possui uma branch `master`, que possui objetivo de manter a versão estável do projeto.
Possui também uma branch para desenvolvimento chamada `devel`, cujo objetivo é manter-se atualizada.
Desta forma nenhum commit deve ser efetuado diretamente nestas branchs. As alterações devem ser criadas inicialmente em branchs de funcionalidades ou de configuração e correção, toda branch de funcionalidade deve ser criada a partir da branch devel. 

A imagem a seguir, ilustra como deve ser a organização das branchs e os eventos de criação e merge de acordo com o [Git Flow](https://leanpub.com/git-flow/read).
[[https://leanpub.com/site_images/git-flow/git-workflow-release-cycle-2feature.png]]

Como pode ser visto, após a etapa de desenvolvimento em uma branch de funcionalidade ser concluída, deve ser submetido um pull request em caso de alguma revisão ou merge da mesma. O pull request deve ser conferido por um membro da equipe e se estiver em conformidade, então o pull request é aceito. 

## Padrão para criação e uso das branches
Deve-se criar novas branches para trabalho seguindo padrão [GitFlow](https://datasift.github.io/gitflow/IntroducingGitFlow.html). Estas devem ser criadas a partir da branch __develop__, e devem seguir a nomenclatura padrão abaixo, redigidas no idioma inglês. 

O código das branchs deve estar sincronizado com alguma Issue do repositório, sendo então o nome padrão para as branchs no formato:  
__tag/i401_validate_username__  
__tag/i397_create_cluster_group__

As __tags__ nos exemplos estão listadas em [Elementos Estruturais](#elementos-estruturais)

### Elementos estruturais

**fix** - Commits do tipo fix indicam que seu trecho de código commitado está solucionando um problema (bug fix), (se relaciona com o PATCH do versionamento semântico).

**feat** - Commits do tipo feat indicam que seu trecho de código está incuindo um novo recurso (se relaciona com o MINOR do versionamento semântico).

**docs** - Commits do tipo docs indicam que houveram mudanças na documentação, como por exemplo no Readme do seu repositório. (Não inclui alterações em código).

**style** - Commits do tipo style indicam que houveram alterações referentes a formatações de código, 
semicolons, trailing spaces, lint... (Não inclui alterações em código).

**refactor** - Commits do tipo refactor referem-se a mudanças devido a refatorações que não alterem sua funcionalidade, como por exemplo, uma alteração no formato como é processada determinada parte da tela, mas que manteve a mesma funcionalidade, ou melhorias de performance devido a um code review.

**build** - Commits do tipo build são utilizados quando são realizadas modificações em arquivos de build e dependências.

**test** - Commits do tipo test são utilizados quando são realizadas alterações em testes, seja criando, alterando ou excluindo testes unitários. (Não inclui alterações em código)

**chore** - Commits do tipo chore indicam atualizações de tarefas de build, configurações de administrador, pacotes... como por exemplo adicionar um pacote no gitignore. (Não inclui alterações em código)

**BREAKING CHANGE** - Commits que possuem o texto BREAKING CHANGE no começo do corpo ou no rodapé, indicam que a modificação que está sendo realizada no commit, possui uma modificiação que quebra a compatibilidade da API, (se relaciona com o MAJOR do versionamento semântico).

## Automatização de Fechamento de Issue
Caso termine sua funcionalidade e deseje fechar a Issue automaticamente é possivel através das palavras chaves na descrição do commit ou pull request:  
`resolves: #numeroDaIssue`  
Em caso de múltiplas issues é necessário replicar o comando:  
`resolves: #numeroDaIssue`  
`resolves: #numeroDaIssue2`  
`resolves: #numeroDaIssue3`  

## Pull-requests tempestivos e permanentes
Nesse projeto adotamos a política dos pull requests tempestivos e permanentes, ou seja, a partir do primeiro commit deve ser criado o pull request de merge da branch da issue com a develop. Esse pull request é, portanto, tempestivo - criado no primeiro commit - e permanente - permanece aberto enquanto o trabalho da issue estiver sendo executado. Além disso, sugere-se, para alterações no frontend, o envio também de prints ou gifs que ajudem a entender o trabalho realizado.

O autor do pull request deve assignar o grupo de revisão: https://github.com/orgs/ejplatform/teams/revision

### Conflitos nos Pull-requests

A branch do PR deve estar sempre atualizado com a branch de desenvolvimento (develop) em caso de conflitos, deve-se realizar um rebase na branch com a develop

### Exceções: commits que podem ser feitos diretamente na devel
- Fix de conteúdo e css (não arquiteturais)
- Tradução
- Cobertura de teste
- Atualizar assets
- Commits de melhoramentos/bugfix de pipeline (que precisam ser commitados na branch do pipeline)

### Validações de produto
As validações de produto acontecem motivadas pelos PRs do develop para a master. Sempre que um revisor fizer o merge dos PRs vindos das branches de issue pra develop, gera um PR correspondente pra master, acionando a validação de produto, focada na release.


