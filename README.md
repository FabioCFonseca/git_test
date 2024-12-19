# Teste Git

## O que é Git:
O Git é um sistema de controle de versão amplamente utilizado para colaborar de forma eficiente em projetos. Ele permite que as equipes acompanhem cada alteração feita no código, possibilitando voltar a versões anteriores, gerenciar o trabalho simultâneo e garantir o desenvolvimento contínuo do projeto.

#### Por que usar o Git?
Em projetos de software de grande escala, sistemas de controle de versão, como o Git, garantem que todas as alterações no código sejam bem documentadas, reversíveis e fáceis de gerenciar. Com o Git, os desenvolvedores podem criar snapshots do código em diferentes estágios, permitindo reverter para versões anteriores quando necessário, além de facilitar a resolução de conflitos.

O uso de branches permite que os desenvolvedores trabalhem simultaneamente no mesmo projeto, desenvolvendo novas funcionalidades ou corrigindo bugs de maneira independente. Depois, essas mudanças podem ser integradas ao projeto principal sem interferir no trabalho dos outros. O Git também mantém um histórico completo de todas as alterações realizadas no código, possibilitando a revisão de modificações anteriores, a identificação de quem fez o quê, e garantindo que nada seja perdido. Esse histórico facilita o entendimento da evolução do projeto ao longo do tempo.

## Commit
O commit é um snapshot do projeto no momento em que foi realizado, capturando todas as mudanças que foram previamente adicionadas à área de stage. Ele armazena não apenas as alterações no código, mas também metadados importantes, como a data e hora (timestamp), o autor, o hash único que identifica o commit, e o hash do commit pai, que estabelece a sequência no histórico de alterações. O commit é o _core_ do versionamento no Git, permitindo que o histórico de mudanças no projeto seja rastreado de forma organizada. Ele garante que cada modificação seja registrada de forma transparente, possibilitando reverter, comparar, e entender a evolução do código ao longo do tempo.

### Commit ideal
Um commit idealmente contém alterações atomizadas, ou seja, pequenas e independentes, que podem ser explicadas de forma concisa em uma frase clara e declarativa. Isso facilita a compreensão e manutenção do histórico de commits, tornando-o um conjunto de mudanças explícitas. A mensagem de commit deve seguir uma estrutura padrão que inclua:

Tipo de commit: Define a natureza da alteração, como fix (correção de bug), feat (nova funcionalidade), ou chore (tarefas de manutenção).
Escopo: Refere-se à área específica do projeto afetada, como camera, parks, ou shorts.
Frase descritiva: Deve ser curta, objetiva, e no tempo verbal presente afirmativo, descrevendo o que o commit faz, por exemplo, "adiciona suporte à câmera", "corrige erro no carregamento de parques".
Essa abordagem mantém o histórico de commits mais limpo e fácil de navegar, permitindo que outros desenvolvedores entendam rapidamente o que foi alterado e o propósito de cada mudança. 

## Branches
Uma branch é uma ramificação do projeto, criada a partir do estado exato de um commit específico. Ao ser criada, ela copia o projeto naquele ponto no tempo, com uma área de stage e repositório local próprios, proporcionando um ambiente de trabalho isolado para o desenvolvedor. Toda branch herda o histórico completo dos commits até o ponto em que foi criada, o que garante que ela mantenha todo o contexto e evolução do projeto até aquele momento.

O principal propósito de uma branch é oferecer um ambiente de desenvolvimento independente, onde novas funcionalidades podem ser implementadas ou bugs corrigidos sem impactar a branch principal, que geralmente contém o código estável e revisado. Depois que as alterações realizadas na branch são concluídas, ela é submetida a uma Pull Request (PR), durante a qual as mudanças são revisadas. Após a aprovação, a branch é mergeada de volta à principal, integrando as novas contribuições ao projeto.

### Merge
O merge permite integrar as mudanças de uma branch em outra, criando um commit com dois pais. O merge 'amarra' as branches, permitindo que a branch que recebeu o merge tenha as alterações de ambas. Quando realizamos um merge entre duas branches, o Git usa a referência de cada uma delas, geralmente o commit mais recente, e encontra um commit anterior comum às duas branches. A partir desse ponto, ele combina as sequências de commits.

### Fast forward merge
O fast-forward merge ocorre quando não há uma bifurcação no histórico entre duas branches que estão sendo mergeadas. Dessa forma, não há necessidade de criar um commit de merge para combinar as branches. O Git simplesmente atualizará a referência da branch que está recebendo o merge para o commit mais recente da outra branch. Esse processo é comumente usado quando se faz um git pull do repositório remoto para atualizar as mudanças de outros desenvolvedores na sua branch local.

### Rebase
O rebase é um comando que, assim como o merge, integra commits de outra branch. A principal diferença é que o rebase move os commits a serem integrados para o topo da branch atual, reescrevendo o histórico de commits, uma vez que a cronologia original é alterada e novos hashes para esses commits são gerados. A vantagem do rebase é que ele proporciona um histórico de commits mais limpo, com as alterações sendo incluídas de forma linear, sem os commits de merge que podem poluir o histórico. 

Porém, o rebase também traz desvantagens como a perda do histórico original, o que pode dificultar a rastreabilidade das mudanças e a análise da evolução do código, especialmente em casos de bugs. Tambem ao usar rebase em branches compartilhadas, há o risco de causar problemas de sincronização entre desenvolvedores, já que o histórico reescrito pode gerar inconsistências ao tentar integrar alterações de outros membros da equipe.

### Cherry pick
O comando cherry-pick permite integrar um commit específico, identificado pelo seu hash, de outra branch à branch atual. Em vez de trazer todo o histórico de uma branch, como acontece com o merge ou rebase, o cherry-pick copia apenas o commit selecionado e o aplica na branch atual. Isso é útil quando você quer incluir uma mudança específica feita em outra branch, sem trazer outros commits que possam não ser relevantes ou desejados.

### Pull
O comando git pull combina dois comandos distintos: o git fetch, que busca as alterações commitadas no repositório remoto e as traz para o repositório local, e o git merge, que mergea essas alterações na sua branch atual. Normalmente, o git merge resulta em um fast-forward merge, quando não há divergências. O git pull é essencial para manter seu repositório local sincronizado com as alterações feitas por outros desenvolvedores no projeto.

### Stash
O stash é uma funcionalidade auxiliar do Git que permite armazenar temporariamente as mudanças feitas no repositório local em uma área isolada. Essa funcionalidade é útil quando é necessário mudar de atividade sem perder as alterações em andamento, que ainda não estão prontas para um commit. Dessa forma, as mudanças podem ser guardadas e reaplicadas posteriormente. Vale destacar que, ao reaplicar as mudanças com o stash, elas também podem gerar conflitos, da mesma forma que acontece em operações de merge.

## Conflitos
Durante o processo de merge, as branches envolvidas podem ter divergido, ou seja, ambas podem conter commits que a outra não possui, muitas vezes no mesmo arquivo ou um arquivo foi editado em uma branch e deletado na outra. Em alguns desses casos, o Git não consegue determinar automaticamente quais alterações devem ser mantidas. Isso gera um merge conflict, momento em que o Git precisa de intervenção manual para resolver como o arquivo deve ficar após o merge. Quando um merge conflict acontece, o Git sinaliza os arquivos problemáticos e marca as áreas conflitantes com delimitadores específicos, mostrando as versões das alterações feitas em cada branch. O desenvolvedor, então, escolhe quais mudanças devem ser aceitas ou combinadas para concluir o processo.


## Estratégias de branching

### GitFlow
O GitFlow é uma estratégia de branching que organiza o ciclo de desenvolvimento em diferentes tipos de branches. Existem duas branches de vida longa: a main e a develop.

Main: contém o código pronto para produção, ou seja, estável e liberado para os usuários finais.
Develop: é a principal branch de integração, onde novas funcionalidades são incorporadas e testadas antes de serem preparadas para lançamento.
A partir da branch develop, são criadas branches de curta duração para o desenvolvimento de funcionalidades específicas, chamadas de feature branches. Essas branches são dedicadas ao desenvolvimento de pequenas funcionalidades, que, quando finalizadas, são integradas de volta à develop ou, em alguns casos, a uma branch intermediária, como uma epic branch, que agrupa várias funcionalidades relacionadas.

Quando a branch develop acumula funcionalidades suficientes para uma nova versão do aplicativo, cria-se uma branch de release. Essa branch é usada para testes finais e estabilização da versão. Após os testes, a branch release é mergeada na main, levando as novas funcionalidades para produção, e também na develop, garantindo que o estado da branch de desenvolvimento reflita as correções e melhorias da nova versão.

Se, após o merge na main, for detectado algum bug em produção, cria-se uma branch hotfix. Essa branch é destinada à resolução rápida do problema. Após a correção, a branch hotfix é mergeada na main, para resolver o bug em produção, e na develop, para que o código de desenvolvimento se mantenha atualizado com a correção.

#### Vantagens e desvantagens
Uma das principais vantagens do GitFlow é que o código passa por diversos reviews e testes antes de ser mergeado em produção. Embora esse processo seja mais demorado, ele garante uma maior qualidade do código final e reduz as chances de erros em produção.

Por isso, o GitFlow é uma estratégia recomendada para equipes grandes ou com menos experiência onde a qualidade e a estabilidade são prioridades. No entanto, sua estrutura pode ser considerada pesada para projetos menores ou equipes que adotam um ciclo de desenvolvimento mais ágil, onde há necessidade de deploys mais frequentes.


## Repositório local, remoto e permissões

### Remote
É uma referência a algum repositório que você deseja realizar push e pulls. Este repositório pode estar hosteado em algum servidor ou até na máquina local em outro diretório.

### Local
O repositório local é uma cópia local do remote em que podemos fazer alterações isoladas localmente e possivelmente subir essas alterações (push) ou recuperar alterações que foram adicionadas ao remote (pull/fetch)

### Permissões

#### Visibilidade do repositório

#### Público
Qualquer pessoa pode ver, clonar ou forkar o repositório, também podem interagir com issues e pull requests

#### Privado
Somente colaboradores convidados podem ver, clonar ou forkar o repositório, além de criar issues e pull requests. É possível criar roles para os colaboradores do projeto para administrar os tipos ações que estes podem realizar no repositório

#### Rulesets





