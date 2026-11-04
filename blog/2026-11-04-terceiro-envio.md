---
title: "Terceiro Envio — 2026-11-04"
authors: [Felipe Duque]
tags: [terceiro-envio]
date: 2026-11-04
---

## Pergunta 1 da fase

*Descreva como as decisões técnicas estão sendo tomadas na sua equipe nesta fase — quem decide, como se chega a um consenso.*

Na Sprint 06, o Thomas documentou no início da sprint quem ficaria com cada issue e a ordem de execução, e o primeiro passo previsto era alinhar os estados e os contratos entre o upload de planos de ensino (#40) e a modelagem que ficou comigo (#53). Na prática, esse alinhamento não aconteceu: as duas issues foram feitas em paralelo, cada uma criou a sua própria migration na tabela de planos, e os dois PRs foram aprovados em dias seguidos, cada um revisado isoladamente. Quando fui conferir a dev depois dos dois merges, o Supabase não subia mais, porque as duas migrations criavam a mesma coluna de status. Além disso, o upload gravava o status em inglês, enquanto o plano da sprint definia os valores em português. Isso mostrou que as grandes decisões são bem registradas pelo líder, mas os detalhes compartilhados, como nomes de colunas e valores de estado, acabam sendo decididos por quem implementa primeiro. Na correção, adaptei a minha migration para reaproveitar as colunas que o upload já tinha criado, mantive os status do plano e marquei os responsáveis pelo back-end no PR, porque o código deles também mudava. Daqui para frente, antes de mexer numa tabela que outra issue também usa, vou comentar na issue quais colunas e estados pretendo usar e esperar o retorno da outra dupla.

## Pergunta 2 da fase

*O que mudou, para você, entre o início da disciplina e este momento — tecnicamente e no seu jeito de trabalhar em equipe?*

Nesta fase, olhando o histórico do repositório, percebi que eu tinha cerca de dez commits, enquanto o Thomas passava de cinquenta. Ao investigar, vi que não era por fazer menos: todas as três issues de segurança da fase anterior (#41, #42 e #43) tinham entrado em um único commit. Na entrega da modelagem dos planos, separei o trabalho em commits independentes, um para a migration, outro para o diagrama e outro para o dicionário de dados, e fiz o mesmo na correção da dev. Tecnicamente, a principal mudança está na forma de testar. No começo do semestre, minha energia ia para fazer o ambiente funcionar; agora, antes de abrir um PR, rodo todas as migrations em ordem sobre dados que já existiam no banco, e foi esse hábito que me fez encontrar o conflito com a migration do upload. Também mudou a forma como uso IA: boa parte do SQL foi escrita com ajuda dela, mas as decisões, como não reaproveitar a coluna professor_id para aluno, e a conferência do resultado ficaram comigo. Concluo que um histórico com commits pequenos mostra o que cada pessoa fez e facilita a revisão dos colegas. Vou manter o hábito de commitar a cada passo concluído, e não apenas no final da tarefa.

## Pergunta 3 da fase

*Compare como você está se sentindo na preparação desta segunda entrega com a forma como se sentiu na primeira.*

Na primeira entrega, descobri na véspera que o formulário de cadastro não estava ligado ao banco, e a sensação foi de insegurança, porque eu tinha considerado a minha parte pronta sem ter visto o fluxo funcionar de ponta a ponta. Na preparação desta segunda entrega, a quebra da dev apareceu dias antes do prazo, e não na véspera, e eu soube onde procurar: reproduzi o erro rodando as migrations em ordem, entendi a causa e testei a correção antes de pedir revisão. A diferença também aparece na organização do repositório: encontrei dois documentos criados direto na main, que gerariam conflito na próxima release, e levei o problema ao Thomas antes que ele aparecesse no dia da entrega. Hoje me sinto mais seguro na parte de banco, mas mais atento aos pontos em que o trabalho de uma dupla encontra o da outra, que é onde os problemas têm aparecido. Para esta entrega, vou subir o sistema completo, banco, back-end e front, pelo menos uma vez por semana, para que esses encontros sejam testados antes da véspera.
