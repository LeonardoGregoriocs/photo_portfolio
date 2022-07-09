# Página utilizada para anotações durante o curso

## COMANDOS

git branch —set-upstream-to=origin/<branch> <outra_branch> → Esse comando informa para o git de qual branch desejamos ficar puxando informações para nossa branch atual, ou seja, no lugar do <branch> poderíamos colocar “master” e ir puxando informações dela pra nossa branch atual.

git log → Esse comando nos o histórico dos commit que foram realizados.

git show <hash_do_commit> → Permite visualizarmos quais mudanças foram feitas no commit que passamos o hash.

- USAR NO MASTER → git revert <numero_do_hash> → Retorna pro commit que passamos no hash, e ignora todas as alterações que foram feita posteriormente ao commit. Mantém o histórico de commit.

- USAR EM BRANCH SEPARADOS → git reset —hard <numero_do_hash> → Retorna pro commit que passamos no hash, e ignora todas as alterações que foram feita posteriormente ao commit. Não mantém o histórico dos commit.

- USAR EM BRANCH SEPARADOS → git reset —soft <numero_do_hash> → Retorna pro commit que passamos no hash, porém todas as alterações voltam para o ambiente de stash, e a partir dali decidimos se queremos adicionar ou não as alterações.

- git commit —amend → Permite alterar a mensagem que escrevemos pro último commit.
- git commit —amend → O mesmo comando permiti adicionar mais alterações em determinado commit mesmo depois de ter dado git commit.
    - O amend é útil somente para quando ainda não enviamos pro repositório remoto ou quando estamos em uma branch separada.

- git cherry-pick <numero_do_hash> → Conseguimos pegar apenas commit específicos de outra branch e trazer para a branch que desejarmos.
    - Para realizar o cherry-pick temos esses passos:
        1. Entrar na branch que está o commit.
        2. Copiar o hash do commit (através do git log).
        3. Voltar para a branch que desejamos trazer esse commit.
        4. Efetuar o comando do cherry-pick.

- git add -p → Usamos esse comando para adicionar apenas algumas partes das alterações que fizemos em um arquivo, para não precisar subir todas as alterações do arquivo.
    - Ao rodarmos o git add -p, temos algumas opções de resposta para o menu que abre no terminal:
        - y → sim, adicione.
        - n → não adicione.
        - q → não adicione e saia imediatamente deste menu.
        - a → adiciona esse e todos os outros que vierem.
        - d → não adiciona esse e nem os outros, parecido com o q, porém ele não sai do menu.
        - j → passar pro próximo.
        - g → passar esse e ver o anterior.
        - s → dividir em partes menores ainda.
        - e → definir manualmente.

git rebase -i HEAD~<numero_que_deseja_voltar> → Este comando é utilizado para quando temos dois commit, mas queremos juntar os dois, ou seja, ter apenas um commite.  O -i abre o terminal e permite termos um terminal interativo. E a segunda opção, passamos quantos commites desejamos voltar.

git commit —fixup <numero_do_hash> → Corrige um commit anterior.
    - Exemplo:
        - Criamos um commit, logo após queremos corrigir algo ou adicionar mais commit, usamos o fixup, vamos supor, que usamos duas vezes e agora queremos unir tudo em um único commit, usamos:
            1. git log, e voltamos até um commit anterior daquele em que queremos juntos, pegamos a hash do commit.
            2. Usamos o comando git rebase -i --autosquash <numero_do_hash> para juntar os commites, irá abrir um novo terminal, onde passaremos as informações queremos.

- Quando temos conflitos, vemos as palavras HEAD (que seria aquilo que temos no nosso repositório local), e ai temos um hash do commit, que é aquilo que veio do repositório remoto e deu algum conflito com aquilo que fizemos.
    - No exemplo do curso, fizemos alterações local no código e depois fizemos no Git Hub (simulando como se outra pessoa tivesse atuado no projeto). Logo após, ao tentarmos dar um “git pull origin master” no nosso código, gerou dois conflitos. Após resolver, damos o comando git add nome_do_arquivo e depois utilizamos o comando “git merge —continue”, onde aparece as informações da correção e o nome do commit, logo após fecharmos, podemos dar um push para o repositório normalmente.

A primeira coisa a ser entendidade sobre o git rebase é que resolve o mesmo problema que o git merge. Ambos são utilizados para integrar, mesclar, misturar alterações para outras, porém, fazem isso de formas diferentes.

git config —global help.autocorrect 1 → Comando nos auxilia na correção de quando escrevemos pequenos erros ortográfico no comando. O git informa que o comando está errado, informa o comando correto.. porém continua, automaticamente, ele corrige e realiza o comando.