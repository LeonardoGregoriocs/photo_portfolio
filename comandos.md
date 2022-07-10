# Página utilizada para anotações durante o curso

## COMANDOS

### GIT LOG -> Visualizar os logs dos commites realizados

* git log → Esse comando nos o histórico dos commit que foram realizados.

* git log personalizados:
    1. git log --pretty=oneline -> Os logs são mostrado em apenas uma linha, traz o hash e a mensagem do commit.

    2. git log --pretty=oneline --graph -> Retorna as informações acima e mais o grafico.

    3. git log --pretty=oneline --graph --all -> Retorn as informações de todas as branch, stages, basicamente tudo.

    #### Filtros dentro do log:

    1. git log --since='Jan 1 2018' -> Podemos filtrar os log através de datas, ou seja, passamos uma data, e ele retorna a partir daquela data informada.

    2. git log --until='Jan 1 2018' -> Podemos filtrar também até aquele dia que passamos, ou seja, tudo que tem antes, e tudo que tem depois é ignorado.

    3. git log --since='Jan 1 2018' --until='Jan 10 2018' -> Podemos usar esse comando quando queremos um periodo, e ai passamos os dois filtros que temos acima.

    4. git log --author="Leonardo" -> Podemos filtrar pelo nome do autor.

    5. git shortlog -> Retorna um log simplificado.

    6. git shortlog -sn -> Retorna um log mais simples ainda, retorna somente o numero de commite e o autor.

    7. git log -<numero_de_commit> -> Retorna os ultimos commites, de acordo com o valor que passarmos em <numero_de_commit>

    * git reflog -> Trabalha em cima das referências. Vai mais fundo que o git log, mostrando a referência de TODA o histório do git. Retorna os commit, rebase, chery-pick, ou seja, literalmente tudo que fizemos no projeto. MUito poderoso e útil, com ele podemos recuperar coisas que deletamos pelo "git reset --hard". **PODE SALVAR MINHA VIDA RS**

### GIT REVERT

    * USAR NO MASTER  → git revert <numero_do_hash> → Retorna pro commit que passamos no hash, e ignora todas as alterações que foram feita posteriormente ao commit. Mantém o histórico de commit.

    * USAR EM BRANCH SEPARADOS → git reset —hard <numero_do_hash> → Retorna pro commit que passamos no hash, e ignora todas as alterações que foram feita posteriormente ao commit. Não mantém o histórico dos commit.

    * USAR EM BRANCH SEPARADOS → git reset —soft <numero_do_hash> → Retorna pro commit que passamos no hash, porém todas as alterações voltam para o ambiente de stash, e a partir dali decidimos se queremos adicionar ou não as alterações.

### GIT AMEND

    * git commit —amend → Permite alterar a mensagem que escrevemos pro último commit.
    * git commit —amend → O mesmo comando permiti adicionar mais alterações em determinado commit mesmo depois de ter dado git commit.
        1. O amend é útil somente para quando ainda não enviamos pro repositório remoto ou quando estamos em uma branch separada.

### CHERRY-PICK

    * git cherry-pick <numero_do_hash> → Conseguimos pegar apenas commit específicos de outra branch e trazer para a branch que desejarmos.
        * Para realizar o cherry-pick temos esses passos:
            1. Entrar na branch que está o commit.
            2. Copiar o hash do commit (através do git log).
            3. Voltar para a branch que desejamos trazer esse commit.
            4. Efetuar o comando do cherry-pick.

### GIT ADD, REBASE E COMMIT

    * git add -p → Usamos esse comando para adicionar apenas algumas partes das alterações que fizemos em um arquivo, para não precisar subir todas as alterações do arquivo.
        * Ao rodarmos o git add -p, temos algumas opções de resposta para o menu que abre no terminal:
            - y → sim, adicione.
            - n → não adicione.
            - q → não adicione e saia imediatamente deste menu.
            - a → adiciona esse e todos os outros que vierem.
            - d → não adiciona esse e nem os outros, parecido com o q, porém ele não sai do menu.
            - j → passar pro próximo.
            - g → passar esse e ver o anterior.
            - s → dividir em partes menores ainda.
            - e → definir manualmente.

    * git rebase -i HEAD~<numero_que_deseja_voltar> → Este comando é utilizado para quando temos dois commit, mas queremos juntar os dois, ou seja, ter apenas um commite.  O -i abre o terminal e permite termos um terminal interativo. E a segunda opção, passamos quantos commites desejamos voltar.

    * git commit —fixup <numero_do_hash> → Corrige um commit anterior.
        * Exemplo:
            * Criamos um commit, logo após queremos corrigir algo ou adicionar mais commit, usamos o fixup, vamos supor, que usamos duas vezes e agora queremos unir tudo em um único commit, usamos:
                1. git log, e voltamos até um commit anterior daquele em que queremos juntos, pegamos a hash do commit.
                2. Usamos o comando git rebase -i --autosquash <numero_do_hash> para juntar os commites, irá abrir um novo terminal, onde passaremos as informações queremos.

    * Quando temos conflitos, vemos as palavras HEAD (que seria aquilo que temos no nosso repositório local), e ai temos um hash do commit, que é aquilo que veio do repositório remoto e deu algum conflito com aquilo que fizemos.
        * No exemplo do curso, fizemos alterações local no código e depois fizemos no Git Hub (simulando como se outra pessoa tivesse atuado no projeto). Logo após, ao tentarmos dar um “git pull origin master” no nosso código, gerou dois conflitos. Após resolver, damos o comando git add nome_do_arquivo e depois utilizamos o comando “git merge —continue”, onde aparece as informações da correção e o nome do commit, logo após fecharmos, podemos dar um push para o repositório normalmente.

        * A primeira coisa a ser entendidade sobre o git rebase é que resolve o mesmo problema que o git merge. Ambos são utilizados para integrar, mesclar, misturar alterações para outras, porém, fazem isso de formas diferentes.

### GIT ARCHIVE -> CRIA ARQUIVO DO REPO
    * git archive → Cria um zip de todo o repositório.
        Nessa comando, podemos passar algumas informações:
            1. git archive <nome_da_branch>

            2. git archive <nome_da_branch> --format=zip -> Ou seja, o formato do arquivo que queremos.

            3. git archive <nome_da_branch> --format=zip --output=master.zip -> Podemos passar o output, para dar o nome do arquivo.

### OUTROS

    * git config —global help.autocorrect 1 → Comando nos auxilia na correção de quando escrevemos pequenos erros ortográfico no comando. O git informa que o comando está errado, informa o comando correto.. porém continua, automaticamente, ele corrige e realiza o comando.

    * git branch —set-upstream-to=origin/<branch> <outra_branch> → Esse comando informa para o git de qual branch desejamos ficar puxando informações para nossa branch atual, ou seja, no lugar do <branch> poderíamos colocar “master” e ir puxando informações dela pra nossa branch atual.

    * git show <hash_do_commit> → Permite visualizarmos quais mudanças foram feitas no commit que passamos o hash.
