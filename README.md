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

## Estratégias de branching

### GitFlow


