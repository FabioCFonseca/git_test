# Teste Git

## O que é Git:

## Git init

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

## Conflitos


## Estratégias de branching

### GitFlow


