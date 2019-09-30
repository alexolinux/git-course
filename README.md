
**GIT/GITHUB para iniciantes**
Este conteúdo tem como objetivo uma abordagem geral do git como ferramenta de versionamento. Descreveremos os principais recursos do git, assim como a configuração inicial do ambiente, para que possamos entender como utilizá-la no nosso dia a dia.

**ENVIRONMENT**
Antes de começarmos a por a "mão-na-massa", é importante configurarmos nosso ambiente com a nossa identidade. Para isso, vamos definir as nossas configurações de ambiente com nossas credenciais a serem utilizadas pelo nosso(s) projeto(s). Abaixo, definiremos nosso nome, nosso e-mail e opcionalmente o nosso editor preferido:

    git config --global user.name "Alex Mendes"
    git config --global user.email "alexmendes@mymail.com"
    git config --global core.editor vim

**OBTENDO INFORMAÇÕES**
Feita a nossa configuração inicial, caso desejarmos checar se tudo está ok, é só validarmos como se segue abaixo:

    git config --list
    git config user.name Alex
    git config user.email alexmendes@mymail.com

**CRIANDO NOSSO REPOSITÓRIO**
Tendo nosso ambiente preparado com nossas configurações, é hora de criarmos o nosso repositório git. Assim sendo, criaremos um repositório que servirá para nosso primeiro projeto no git.
Para criarmos nosso repositório de origem em nossa máquina, executaremos o comando "git init" para iniciarmos nosso repositório git local. No meu caso, antes eu criei uma estrutura de diretórios **/git/git-course**, e dentro desse diretório inicializei/executei o comando abaixo:

    git init
    Initialized empty Git repository in /git/git-course/.git/

Será criado um subdiretório **.git**, dentro dele estarão armazenadas as configurações de atividades e rastreio do seu projeto.

**CICLO DE VIDA DE ARQUIVOS NO git**
Ao se trabalhar com o git, é importante entendermos o conceito por trás desta ferramenta de versionamento. O **git** possui um ciclo de vida desde a alteração ou inclusão de arquivos no código do repositório, lembrando que neste processo existe transições entre o local que você trabalha (suas máquinas locais) e o servidor centralizado do git (github, gitlab, bitbucket, etc). Este ciclo ou transporte de mudanças dos arquivos passa por determinados estágios:
> << UNTRACKED > UNMODIFIED > MODIFIED > STAGED >><< UNTRACKED > UNMODIFIED > MODIFIED > STAGED >>

[![git - The lifecycle of the status of your files.](https://git-scm.com/book/en/v2/images/lifecycle.png "git - The lifecycle of the status of your files.")](https://git-scm.com/book/en/v2/images/lifecycle.png "git - The lifecycle of the status of your files.")
###### 1. ciclo de vida de status dos arquivos.

Entre os estados do git, é importante entendermos os três principais:
1. **committed:** Estado consolidado ou popularmente "comitado".
2. **modified:** Significa que arquivo foi modificado, mas ainda deve ser adicionado para ser comitado.
3. **staged:** O arquivo já está preparado para o próximo commit.
(*Caso queira entender mais sobre os estados, recomendo acessar https://git-scm.com/book/pt-br/v1/Git-Essencial-Gravando-Altera%C3%A7%C3%B5es-no-Reposit%C3%B3rio para um entendimento mais aprofundado.*)

**GIT STATUS**
Ok... Como saber o estado dos arquivos do meu repositório git? Simples... Executa aí:

    git status
	Nothing added to commit but untracked files present (use "git add" to track)
O status acima nos sinaliza que não tem nada para ser comitado, sugerindo que adicionemos algum arquivo para commit.

**ADD FILE TO GIT:**
Agora vejamos como adicionar um arquivo para ser comitado ao nosso servidor git:

    git add README.md
    new file:   README.md
Acabamos de adicionar um arquivo para que possa ser comitado **\o/**.

OBS:
> Sempre que houver alterações de arquivos, DEVEMOS USAR "git add" NOVAMENTE (antes do commit -> Staged).

**GIT COMMIT**
Chegamos ao famoso **git commit**...  Com ele registramos as mudanças no repositório.

    git commit -m "Add README.md"
    [master (root-commit) 661c72d] Add Readme.md
    1 files changed, 2 insertions(+), 0 deletions(-)
    create mode 100644 Readme.md

**git checkout & git reset**
Agora aprenderemos como reverter mudanças do código para a etapa anterior:

- **git checkout** - Ele é utilizado para reverter etapas antes de ações de commit.
- **git reset** <--level> - Utilizado para reverter etapas depois de ações de commit.

**HOW TO**
Exemplificando:

01 - Antes de execução 'git add' (staged phase):

(use "git checkout -- ..." to discard changes in working directory)

    git checkout <FILE>

02 - Depois de 'git add' (staged phase (ready to commit))

(use "git reset HEAD ..." to unstage)

    git reset HEAD <FILE>

**UM POUCO MAIS DE git - "git reset"**

* **git reset** levels:
 
    git reset [--mixed | --soft | --hard | --merge | --keep] [-q] []

NOTE: 
> git reset sempre faz a chamada para o HASH anterior ao commit. 

**DETALHAMENTO:**

--soft *(CANCELS COMMIT, TAKE AWAY STAGE)*
Não toca no arquivo de índice nem na árvore de trabalho, mas exige que estes estejam em boas condições. Isso deixa todos os seus arquivos no estado  "Changes to be committed".
    EX.:
    git reset --soft e3131b3f718e17c2014c528ba81e67dd16e232e4

--mixed *(CANCELS COMMIT, KEEP OUT STAGE(KEEP UNSTAGED))*
Redefine o índice, mas não a árvore de trabalho (ou seja, os arquivos alterados são preservados, mas não marcados para commit) e relata o que não foi atualizado. Esta é a ação default.
	EX.:
	git reset --mixed e3131b3f718e17c2014c528ba81e67dd16e232e4

--hard *(CANCELS COMMIT, UNDO ALL COMMIT CHANGES)*
Corresponde a árvore de trabalho e o índice àquele da árvore que está sendo alternada.
> "Quaisquer alterações nos arquivos "tracked" na árvore de trabalho desde o commit serão perdidas."

**GIT LOGS - OPTIONS**
**git log** é o nosso visualizador de históricos de ações e mudanças ocorridas no nosso repositório git.
***Executar o comando no DIRETÓRIO/REPOSITÓRIO de trabalho (onde contém o .git/)***

    git log
    commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
    Author: Alex <alexmendes@mymail.com>
    Date:   Mon Nov 5 23:36:04 2018 -0200

**RECURSOS DO git log**

    git log --decorate
    commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX (HEAD, master)
    Author: Alex <alexmendes@mymail.com>
    Date:   Mon Nov 5 23:36:04 2018 -0200
    
    Add Readme.md

**LOG - FILTRO POR AUTOR**

    git log --author="Alex"

**LOG BREVE COM shortlog**

    git shortlog
    Alex (2):
    
    Add Readme.md
    Updating Readme.md

    git shortlog -sn
	2  Alex

**LOG COM ÁRVORE GRÁFICA**

    git log --graph
        * commit ec98347a9312a0ec51c2967546ca48ba42c5a65cxX
        | Author: Alex <alexmendes@mymail.com>
        | Date:   Tue Nov 6 20:39:19 2018 -0200
        |
        |     Updating Readme.md
        |
        * commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
        Author: Alex <alexmendes@mymail.com>
        Date:   Mon Nov 5 23:36:04 2018 -0200

	Add Readme.md

**DETALHAMENTO PELA HASH DO commit**

    git show <HASH_COMMIT>

    git show 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
    commit 661c72d4470e6c59bb38e23e1af5eaae716d0baaxX
    Author: Alex <alexmendes@mymail.com>
    Date:   Mon Nov 5 23:36:04 2018 -0200

	Add Readme.md

**OBTENDO ALTERAÇÕES COM O diff**

    git diff

    diff --git a/Readme.md b/Readme.md

    new file mode 100644
    index 0000000..55e9705
    --- /dev/null
    +++ b/Readme.md
    @@ -0,0 +1,2 @@
    +# Github
    +Basic Study Repo GIT/GITHUB.
        git CHANGES
        git diff
        diff --git a/Readme.md b/Readme.md
    index fe17549..f401c3e 100644
    --- a/Readme.md
    +++ b/Readme.md
    @@ -1,4 +1,8 @@
    -###########
    -# Github ##
    -#06-11-2018
    +#########################
    +# Github                #
    +# https://git-scm.com/  #
    +# 06-11-2018            #
    +#_______________________#
    +#########################
    +
    Basic Study Repo GIT/GITHUB.

**OBTENDO ALTERAÇÕES SOMENTE PELO NOME**

    git diff --name-only
    	Readme.md

**TRABALHANDO COM REPOSITÓRIOS REMOTOS**
Até aqui foi visto o git de forma local, levando em consideração enviar alterações e novo conteúdo de nossa máquina local para o servidor remoto. É hora de aprendermos o contrário...
Então tá! Mas como faço para atualizar meu repositório local a partir do meu repositório remoto?

Vamos criar um novo repositório adicionando um README.md:

    git init
	echo "# git-course" >> README.md
	git add README.md
	git commit -m "first commit"
	git remote add origin git@github.com:alexmbarbosa/git-course.git 
	git push -u origin master
Aqui nós iniciamos um repositório git, adicionamos um arquivo README.md com uma linha "# git-course", fizemos o commit. O "git remote add origin" quer dizer que adicionamos essa nossa nova mudança para um repositório já existente no github (git-course.git). A seguir iremos entender como checar essas mudanças (git remote -v). Então fica calmo! ;)

Fazendo um "push" para um repositório existente da nossa linha de comando:

    git remote add origin git@github.com:alexmbarbosa/git-course.git
    git push -u origin master
No git push, estamos "empurrando" nossas modificações para esse repositório na Branch **master** (veremos branches mais pra frente).

**CHECANDO A EXISTÊNCIA DE UM REPOSITÓRIO**

    git remote show origin <- Output Command.

**VERBOSE MODE**
Tú lembras que falei sobre como checar essas mudanças remotas? Então, vamos digitar:

    git remote -v

    origin git@github.com:alexmbarbosa/git-course.git (fetch)
    origin git@github.com:alexmbarbosa/git-course.git (push)

**RECEBENDO MUDANÇAS DE CÓDIGO DE UM REPOSITÓRIO**
Agora vamos aprender o inverso... Trazer as mudanças de um repositório remoto para nosso repositório local. Isso sempre será necessário quando outros usuários fizerem outras alterações no repositório remoto. Aí então teremos que atualizar nosso repositório local para posteriormente enviar nossos commits.

    git pull [<options>] [<repository> [<refspec>…]]

O comando git pull incorpora  mudanças de um repositório remoto na branch atualmente em uso.
***Em seu modo padrão, git pull é uma abreviação de git fetch, seguida por git merge FETCH_HEAD***. Mas isso é outra história que requer maior aprofundamento (segue a dica de leitura: https://git-scm.com/book/pt-br/v1/Git-Essencial-Trabalhando-com-Remotos).

    git pull
    remote: Enumerating objects: 17, done.
    remote: Counting objects: 100% (17/17), done.
    remote: Compressing objects: 100% (10/10), done.
    remote: Total 15 (delta 5), reused 0 (delta 0)
    Unpacking objects: 100% (15/15), done.
    From http://github.com/ga/git-course
       ca066cb..c3de5a7  master     -> origin/master
    Updating ca066cb..c3de5a7
    Fast-forward
     README.md | 13 +++++++++++--
     1 file changed, 11 insertions(+), 2 deletions(-)

**CLONANDO PROJETOS git**
Uma coisa que todo sysadmin já fez na vida, mesmo que ainda não tenha utilizado aprofundadamente o git, foi fazer um tal **git clone** de algum projeto por aí... Então vamos entender o que é isso.

**git clone** - Clona um repositório de um projeto remoto para um novo diretório local. Geralmente usado quando você precisa puxar um repositório de um projeto remoto para sua máquina, afim de trabalhar nele ou até mesmo utilizá-lo para algum fim.

**git clone PROTOCOLS**
Com o git clone, é possível trabalhar com alguns protocolos, além do próprio git:

    * ssh://[user@]host.xz[:port]/path/to/repo.git
    * git://host.xz[:port]/path/to/repo.git
    * http[s]://host.xz[:port]/path/to/repo.git
    * ftp[s]://host.xz[:port]/path/to/repo.git

Example:

    git clone user@host.xz:path/to/repo.git/

**COMPREENDENDO CONCEITOS DE  "FORK"**
**fork** é uma cópia de um repositório existente. O fork de um repositório permite fazer uma cópia de um repositório de alguém sem afetar o projeto original.
Geralmente, forks são usados para propor alterações no projeto de outra pessoa ou para usar o projeto de outra pessoa como ponto de partida para sua própria idéia.

![alt text](https://help.github.com/assets/images/help/repository/fork_button.jpg)
######2. Barra com a option FORK.

**O QUE É BRANCH?**
**Branches** são ponteiros para um instantâneo de suas alterações. Quando você deseja adicionar um novo recurso ou corrigir um erro - não importa quão grande ou pequeno - você gera uma nova ramificação (gera um branch) para encapsular suas alterações. É uma maneira de proteger seu projeto de grandes e significativas mudanças que podem causar impacto no conteúdo projeto de uma maneira geral.
Isso dificulta a mesclagem do código instável na base de código principal e oferece a oportunidade de limpar o histórico futuro antes de mesclá-lo na branch principal (branch master).

**COMANDO git branch**
**git branch** - Lista, cria, ou deleta branches.
Com este comando vamos criar, listar, renomear e deletar branches.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:746be214-eb99-462c-9319-04a4d2eeebfa/01.svg)
######3. Árvore de branches

git branch não permite alternar entre as branches ou reunir um histórico de um fork anterior novamente. Por esta razão o git branch está fortemente integrado com os comandos **git checkout** e **git merge** (que veremos em seguida).

**git branch COMMON OPTIONS**
Lista todos os branches em seu repositório. Este é o sinônimo de **git branch --list**.

    git branch

Abaixo criaremos uma branch <branch>:

	git branch <branch>

Com a opção **-d** nós deletamos a branch.
Esta é uma operação "segura", pois o git nos impede que excluemos  a branch se houver mudanças nela "não mergeadas".

    git branch -d <branch>

Com a opção **-D** é possível *forçar o delete* da branch especificada. Só use esse comando se você realmente deseja descartar todos os commits associados à ele na linha de desenvolvimento: 

    git branch -D <branch>

**DELETANDO BRANCHES REMOTAS**
Agora vamos deletar branches remotas em nosso git. Para deletar uma branch remota, nós não usaremos o comando **git branch**, ao invés disso, usaremos o **git push** com a flag --delete: 

    git push <remote_name> :<branch_name>
    git push origin --delete feature/login

Renomeia a branch atual para <era1branch>:
    git branch -m <era1branch>

Liste todas as branches remotas:
    git branch -a

Crie uma nova branch <newbranch> referenciando <start-point>, and confira:
    git checkout -b <newbranch> <start-point>

**NOTAS IMPORTANTES SOBRE BRANCHES**
Se você criar uma branch que você queira fazer checkout imediatamente, é só usar o comando **git checkout -b**. A opção **-b** cria a nova branch e já te coloca nela. **;)**
As opções **--contains, --no-contains, --merged and --no-merged** servem para 4 diferentes propósitos:
    **--contains <commit>** é usada para encontrar todos branches que precisarão de atenção especial se <commit> estiver em status "rebased ou amended", desde que os  branches contenham o <commit> especificado.
    **--no-contains <commit>** é o inverso disso, ou seja, branches que não contenham a <commit> especificada.
    **--merged** é usada para encontrar todas branches que possam ser excluídas com segurança, desde que estas estejam totalmente contidas por **HEAD**.
    --no-merged é usada para encontrar branches que estão candidatadaspara merge pelo **HEAD**, desde que não estejam totalmente contidas pelo **HEAD**.

**MANIPULANDO BRANCHES**
**git checkout** - Alterna branches ou restaura arquivos na árvore de trabalho.

O **git checkout** atualiza nossa árvore de arquivos, correspondendo com a versão do índice ou árvore especificada. Se nenhum caminho for fornecido, o git checkout também fará um update no HEAD, definirá a branch especificada como o branch atual
    git checkout <branch>

Para se preparar para trabalhar no <branch>, alterne para ele atualizando o índice e os arquivos na árvore de trabalho e pelo apontamento da HEAD na branch.
As modificações locais nos arquivos da árvore de trabalho são mantidas, para que possam ser confirmadas no <branch>.
Se o <branch> não for encontrado mas existir uma branch rastreada no repositório remoto, nós chamaremos a branch remota <remote> referindo-se ao nome dessa branch:
    git checkout -b <branch> --track <remote>/<branch>

Especificar **-b** culminará em uma nova branch a ser criada como se o **git branch** fosse chamado e então verificado em seguida.
    git checkout -b|-B <new_branch> [<start point>]

Se -B for dado, <new_branch> será criada caso esta não exista; de outra forma será resetada.

**UNINDO BRANCHES**
Existem 2 maneiras diferentes de unir branches. Elas são:
-   git merge
-   git rebase

**git merge**
**git merge** irá combinar múltiplas sequências de commits num histórico unificado. Na maioria dos casos, o **git merge** geralmente é utilizado para combinar duas branches. Nos exemplos a seguir, veremos uma espécia de merging pattern, nestes cenários teremos dois ponteiros de commits, indo para uma base em comum entre eles:

![alt text](https://wac-cdn.atlassian.com/dam/jcr:86eba9ec-9391-45ea-800a-948cec1f2ed7/Branch-2.png)
######4.Um exemplo de git merge.

Invocando este comando ele fará o merge da feature branch especificada na branch atual, assumindo a master. O git determinará o algoritmo de mesclagem automaticamente:

![alt text](https://wac-cdn.atlassian.com/dam/jcr:83323200-3c57-4c29-9b7e-e67e98745427/Branch-1.png)
######5.Um exemplo de git merge.

**merge commits** são únicas em relação a outras no fato de terem dois commits pais. Ao criar um merge consolidado, o git tentará mesclar automaticamente os históricos separados para você.

**git merge - ANTES E DEPOIS**

![alt text](https://wac-cdn.atlassian.com/dam/jcr:91b1bdf5-fda3-4d20-b108-0bb9eea402b2/08.svg)
######6.git merge (antes e depois).

O código abaixo cria uma nova branch, adiciona dois commits e a integra à linha principal com uma merge "fast-forward".

    # Iniciar uma nova feature:
    git checkout -b new-feature master
    # Editar alguns arquivos, add e comitar:
    git add <file>
    git commit -m "Start a feature"
    # Editar alguns arquivos, add e comitar:
    git add <file>
    git commit -m "Finish a feature"
    # Fazer merge numa nova feature branch:
    git checkout master
    git merge new-feature
    git branch -d new-feature

**"MERGING" com git merge**
Como vimos, **merge** acontece ao combinarmos duas branches. O git pegará dois (ou mais) ponteiros de commits e tentará encontrar uma base comum entre eles.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:e229fef6-2c2f-4a4f-b270-e1e1baa94055/02.svg)

![alt text](https://wac-cdn.atlassian.com/dam/jcr:2d3aef7f-6e1d-4e39-a5a5-97dd7714fdd2/what-is-a-merge.gif)

**git rebase**
Vimos bastante sobre o git merge, agora vamos entrar no **git rebase**. "Rebasing" é o processo de mover ou combinar uma sequência de commits *para uma nova base commit*. Ele é mais útil e facilmente visualizado no contexto de uma *feature branching workflow* (neste conceito, um novo branch é criado para cada nova feature). Este workflow será visto a seguir:

![alt text](https://wac-cdn.atlassian.com/dam/jcr:e4a40899-636b-4988-9774-eaa8a440575b/02.svg)
######7. git rebase

De uma perspectiva de conteúdo, o rebasing está alterando a base de sua branch de um commit para outro, fazendo parecer que você criou sua branch a partir de um commit diferente. Internamente, o git realiza isso criando novos commits e aplicando-os à base especificada.
*É muito importante entender que, embora a *branch* pareça a mesma, ela é composta de commits novos*.

**AS REGRAS DO git rebase**
Rebase tem a vantagem de que não há outros novos merges commits criados, confundindo o meio de campo. No entanto, como o HEAD não é um descendente de um pre-rebase HEAD comitado, o rebasing pode ser problemático. **Tentando esclarecer**, o **git rebase** tem a vantagem de *não criar um novo commit para "mergear" ("commit de merge")*.

Mas como nem tudo são flores, deve-se tomar cuidado com o rebase... 

**PREVENINDO PROBLEMAS COM git rebase**
- REGRA 1: Nunca faça rebase que foi enviado pararepositórios públicos.
- REGRA 2: Comitar  quando a branchmuda no repositório remoto.

O exemplo a seguir combina o **git rebase** com o **git merge** para manter o histórico do projeto linear:

    # Inicie uma new feature
    git checkout -b new-feature master
    # Edite os arquivos
    git commit -a -m "Start developing a feature"

No meio da nossa feature, 
In the middle of our feature, percebemos que há uma falha de segurança em nosso projeto:

    # Criamos uma branch "hotfix" baseada nanossa  branch "master"
    git checkout -b hotfix master
    # Editamos arquivos
    git commit -a -m "Fix security hole"
    # Fazemos o merge novamente na branch master
    git checkout master
    git merge hotfix
    git branch -d hotfix
Após o merge da branch hotfix para a master, nós temos uma cópia do histórico de nosso projeto. Ao invés de usarmos o git merge nós integraremos a feature branch com o git rebase, mantendo o histórico linear:

    git checkout new-feature
    git rebase master

Isso move a nova feature para a ponta da branch master, o que nos permite fazer uma mesclagem de fast-forward padrão na master:

    git checkout master
    git merge new-feature

**RECAPITULANDO: MERGE vs REBASE**

**Merging**

Quando você executa o **git merge**, sua branch HEAD gera um novo commit, preservando a ancestralidade de cada histórico de commit.

![alt text](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/673b91456bdc6fd454c5ad203f825568/git-merge-2.png)

Fast forward merge is a type of merge that doesn't create a commit, instead, it updates the branch pointer to the last commit.

Pros:

1- Simple to use and understand.
2- The commits on the source branch remain separate from other branch commits. This separation can be useful in the case of feature branches, where you might want to take a feature and merge it into another branch later.
3- Existing commits on the source branch are unchanged and remain valid. It doesn’t matter if they have been shared with others.

Cons:

1- History can become polluted by lots of merge commits.
2- Visual charts of your repository can have non-informative branch lines.

**Rebasing**

The rebase re-writes the changes of one branch onto another without creating a new commit.
For every commit that you have on the feature branch and not in the master, a new commit will be created on top of the master. It will appear as if those commits were written on top of master branch all along.

![alt text](https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/5ade4f7276bc6ad18dad4b6078950ac9/git-rebase.png)
######8.git merge.

Pros:

1- Simplifica seu histórico e gráficos visuais.

Cons:

1. No Git, você pode enviar commits por push que você deseja um rebase posteriormente (como backup), mas apenas se for para uma branch remota que *somente você usa*. Se alguém fizer um checkout nessa branch e você querer o rebase posteriormente, isso ficará *muito confuso*.

2. Cada commit é reorganizada em ordem e um conflito interromperá o processo de reestruturação múltipla. havendo um conflito, você deve resolvê-lo primeiro para continuar o rebase.

**git merge ou git rebase? Qual devo usar?**

Os seguintes fatores devem ser considerados ao optar por uma dessas opções:
1. Se você planeja reintegrar uma feature branch completa, *use merge*.
2. Se você já empurrou (push) a branch na qual está trabalhando, então *não deve usar rebase e sim o merge*. Para branches que não foram enviadas, *rebase, test e merge*.
3. Se você estiver trabalhando em uma branch compartilhada ou em um projeto open source, juntamente com muitos outros desenvolvedores fora da sua equipe, *não use rebase*. Já que o rebase destruirá branches de outros desenvolvedores acarretando em  repositórios inconsistentes.
4. Se você acha que há uma chance de querer reverter algumas alterações, *use merge*, pois reverter um *rebase é consideravelmente difícil em comparação com a reversão de merge*.

**.gitignore**
Geralmente em nossos repositórios, geralmente existem algums arquivos que não devem ou não faz nenhum sentido que sejam enviados para nosso repositório remoto, como arquivos binários ou até mesmo arquivos confidenciais (contendo registros de passwords). É para isso que existe o **gitignore**. 
**gitignore** - Especifica arquivos que não devem ser rastreados para envio ao repositório remoto (devem ser *ignorados*).

![alt text](https://wac-cdn.atlassian.com/dam/jcr:75f75cb6-a6ab-4f0b-ab29-e366914f513c/hero.svg)
######9.gitignore

O git enxerga todos os arquivos em sua cópia de trabalho como uma das três coisas:

- tracked - um arquivo que foi previamente para estado **staged ou commited**;
- untracked - um arquivo que não foi para estado **staged ou commited**;
- ignored - um arquivo que o git foi instruído a ignorar.

This Example below in order to exclude everything except a specific directory foo/bar (note the /* - without the slash, the wildcard would also exclude everything within foo/bar):

O exemplo abaixo tem como objetivo ignorar tudo, com exceção do diretório **foo/bar**:

    $ cat .gitignore
    # exclude everything except directory foo/bar
    /*
    !/foo
    /foo/*
    !/foo/bar
    
**NOTA:**
> Ratificando, o propósito do arquivo .gitignore é garantir que certos arquivos não rastreados pelo git *permaneçam não rastreados*.
> Para parar de rastrear um arquivo atualmente rastreado, use **git rm --cached**.

**git stash**
git stash - Sua função como sugere o **https://git-scm.com** é tirar o estado sujo do seu diretório de trabalho — isto é, seus arquivos modificados que estão sendo rastreados e mudanças na área de seleção — e o salva em uma pilha de modificações inacabadas que você pode voltar a qualquer momento.
Use git stash quando desejar gravar o estado atual do diretório de trabalho e do índice, mas desejar voltar para um diretório limpo. O comando salva suas modificações locais e reverte o diretório de trabalho para corresponder ao commit HEAD.

    $ git status
    On branch master
    Changes to be committed:
    new file: style.css
    Changes not staged for commit:
    modified: index.html
    $ git stash
    Saved working directory and index state WIP on master: 5002d47 our new homepage
    HEAD is now at 5002d47 our new homepage
    $ git status
    On branch master
    nothing to commit, working tree clean

Nesse ponto, você é livre para fazer alterações, criar novos commits, alternar branches e executar quaisquer outras operações do git; volte e aplique novamente o seu stash quando estiver pronto.

**Dicas para uso do git stash**

>Se você dropar ou limpar as entradas stash por engano, elas não poderão ser recuperadas pelos mecanismos de segurança normais. No entanto, você pode tentar o seguinte método para obter uma lista de entradas stash que ainda estão no seu repositório, mas que não são mais acessíveis:

    git fsck --unreachable |
    grep commit | cut -d\  -f3 |
    xargs git log --merges --no-walk --grep=WIP

**git aliases**
**git alias** fornece facilmente um alias para cada comando usando o git config. Aqui estão alguns exemplos que você pode querer configurar:

    $ git config --global alias.co checkout
    $ git config --global alias.br branch
    $ git config --global alias.ci commit
    $ git config --global alias.st status

**git tag**
Eis aqui um recurso muito útil e importante, também muito utilizado entre os utilizadores que mantém as boas práticas em seus códigos. O git tem a capacidade de marcar pontos específicos no histórico de um repositório como sendo importantes. Normalmente, as pessoas usam essa funcionalidade para marcar pontos de releases (v1.0, v2.0 e assim por diante). Nesta seção, você aprenderá como listar tags existentes, como criar e excluir tags e quais são os diferentes tipos de tags.

**LISTANDO TAGS**
Listar as tags existentes no git é bem simples. Basta digitar git tag (com opcional -l ou --list):

    $ git tag
    v1.0
    v2.0

>Este comando lista as tags em ordem alfabética; a ordem em que são exibidas não tem importância real.

Você também pode procurar por tags que correspondam a um padrão específico. O repositório de origem do git, por exemplo, contém mais de 500 tags. Se você estiver interessado apenas em buscar a release 1.8.5, execute:

    $ git tag -l "v1.8.5*"
    v1.8.5
    v1.8.5-rc0
    v1.8.5-rc1
    v1.8.5.1
    v1.8.5.3

**CRIANDO TAGS**
git suporta 2 tipos de tags: **lightweight and annotated.**
Uma lightweight tag é muito parecida com uma branch que não muda. É apenas um ponteiro para um commit específico.

Annotated tags, no entanto, são armazenadas como objetos completos no banco de dados do git. Eles são contém o nome, o email e a data do marcador; possuem uma mensagem de marcação; e podem ser assinados e verificados com o GNU Privacy Guard (GPG). Geralmente, é recomendável que você crie tags anotadas para ter todas essas informações; mas se você deseja uma tag temporária ou, por algum motivo, não deseja manter as outras informações, é só usar a lightweight tag.

**ANNOTATED TAGS**
Criar uma tag anotada no git também é bem simples. A maneira mais fácil é especificá-la quando você executar o comando git tag:

    $ git tag -a v1.4 -m "my version 1.4"
    $ git tag
    v0.1
    v1.3
    v1.4

The -m especifica uma "tagging message", a qual é armazenada com a tag. Se você não especificar uma mensagem para a tag, o git lança seu editor para que você possa digitá-lo.

**DELETANDO TAGS**
Para excluir uma tag no seu repositório local, você pode usar **git tag -d <tagname>**. Por exemplo, podemos remover nossa tag acima, da seguinte maneira:

    $ git tag -d v1.4-lw
    Deleted tag 'v1.4-lw' (was e7d5add)

Observe que isso não remove a tag de nenhum servidor remoto. Existem duas variações comuns para excluir uma tag de um servidor remoto.
A maneira de interpretar o exposto acima é lê-lo como o valor nulo antes que os dois pontos sejam empurrados para o nome do tag remoto, excluindo-o efetivamente.

A segunda maneira (e mais intuitiva) para deletar uma tag remota:

    $ git push origin --delete <tagname>

Para excluir tags remotas, a primeira variação é:

    git push <remote> :refs/tags/<tagname>:
    $ git push origin :refs/tags/v1.4-lw
    To /git@github.com:schacon/simplegit.git
        - [deleted]         v1.4-lw

E a segunda:

    git push --delete origin tagname
    git tag -d tagname

**git revert**

git revert - Utilizado para reverter alguns commits existentes.

Dado um ou mais commits existentes, reverta as alterações introduzidas pelos patches relacionados e registre alguns novos commits que as registrem.
Isso requer que sua árvore de trabalho esteja limpa (nenhuma modificação do commit HEAD).
O comando git revert pode ser considerado um "undo", no entanto, não é uma operação undo tradicional. Em vez de remover a confirmação do histórico do projeto, ele descobre como inverter as alterações introduzidas pelos commits e anexa um novo commit com o conteúdo inverso resultante.

![alt text](https://wac-cdn.atlassian.com/dam/jcr:b6fcf82b-5b15-4569-8f4f-a76454f9ca5b/03%20(7).svg)
######10.git revert.

**git revert exemplos:**
Revertendo alterações especificadas pelo quarto último commit no HEAD e criando um novo commit com as alterações revertidas:

	git revert HEAD~3

Revertendo as alterações feitas por commits do quinto último commit na branch master (incluída) para o terceiro último commit em master (incluída), mas não cria nenhum commit com as alterações revertidas. A reversão modifica apenas a árvore de trabalho e o índice.

	git revert -n master~5..master~2
	
**Resetting vs Reverting**

É importante entender que o git revert desfaz um único commit - ele não "reverte" de volta ao estado anterior de um projeto, removendo todos os commit subsequentes.
*No git, isso é chamado de reset, e não revert, ok?*

![alt text](https://wac-cdn.atlassian.com/dam/jcr:a6a50d78-48e3-4765-8492-9e48dec8fd2f/04%20(2).svg)
######11.git revert

Bem, por enquanto é isso!

**REFERÊNCIAS:**

	- <https://git-scm.com/book/pt-br/v1/Ramifica%C3%A7%C3%A3o-Branching-no-Git-O-que-%C3%A9-um-Branch>
	- <https://www.udemy.com/git-e-github-para-iniciantes>
	- <https://git-scm.com/book/pt-br/v1/Primeiros-passos-No%C3%A7%C3%B5es-B%C3%A1sicas-de-Git>
	- <https://br.atlassian.com/git/tutorials/>
	- <https://git-scm.com/docs/user-manual.htmlh>
    	- <http://ndpsoftware.com/git-cheatsheet.html>
    	- <https://www.git-tower.com/learn/git/faq/delete-remote-branch>
	- <https://pt.stackoverflow.com/questions/80583/qual-%C3%A9-a-diferen%C3%A7a-entre-um-branch-e-uma-tag>
