---
title: "Segundo Envio — 2026-10-07"
authors: [Felipe Duque]
tags: [segundo-envio]
date: 2026-10-07
---

## Pergunta 1 da fase

*Olhando para a release que acabou de ser entregue, o que você diria que funcionou bem e o que não funcionou na sua equipe?*

Na véspera da Release 1, o Thomas perguntou no grupo se a distinção entre aluno e professor já estava funcionando, e nem eu nem o Luis soubemos responder com certeza. Fui testar o fluxo inteiro e descobri que o banco estava correto, com a regra do e-mail institucional pronta e testada, mas o formulário de cadastro não enviava nada: os campos não guardavam o que era digitado e o botão "Criar Conta" apenas mudava de página. Na prática, o único jeito de entrar era pelo Google, e por ele todos nasciam como estudantes. O que funcionou foi a divisão em duplas, que permitiu que cada área avançasse ao mesmo tempo; o que não funcionou foi a ligação entre elas, já que a tela foi feita antes do banco existir e ninguém ficou responsável por conectar as duas pontas. Como o login estava sob responsabilidade da minha dupla, essa ligação também era nossa. Concluo que entregar a minha parte não significa que a funcionalidade esteja funcionando. Para a próxima release, vou testar cada fluxo de ponta a ponta, da tela até o banco, antes de considerar uma tarefa concluída.

## Pergunta 2 da fase

*Que responsabilidades técnicas você tem assumido, e como você tem lidado com elas?*

Minha principal responsabilidade técnica nesta fase foi a tabela de perfis, que define se o usuário é estudante ou professor. Decidimos em grupo que só poderia ser professor quem tivesse e-mail institucional, e implementei essa regra dentro do próprio banco, e não apenas na tela, já que no nosso projeto o navegador conversa diretamente com o Supabase e qualquer validação feita só no front pode ser contornada. Ao testar, percebi que uma verificação simples por "termina em unb.br" deixaria passar qualquer e-mail @aluno.unb.br, o que transformaria todo aluno com e-mail institucional em professor. Só encontrei esse problema porque testei os casos que deveriam falhar, e não apenas os que deveriam funcionar. Antes disso, passei boa parte da semana só tentando fazer o ambiente rodar: Docker sem a virtualização ativada, portas do Supabase alteradas e um arquivo .env corrompido por caracteres invisíveis. Concluo que lidar com uma responsabilidade técnica envolve tanto a lógica quanto o ambiente em que ela roda. Vou manter o hábito de testar os casos de abuso e passar a documentar os problemas de ambiente que resolver, para que outro colega não perca o mesmo tempo.

## Pergunta 3 da fase

*Que lacunas técnicas ainda te incomodam, e o que você tem feito, ou pretende fazer, a respeito?*

Uma lacuna que ainda me incomoda é a dificuldade de diagnosticar sozinho problemas de infraestrutura. Quando o login com Google falhou, a tela mostrava apenas "conexão recusada", e só entendi a causa, os containers ainda rodando na porta antiga enquanto a configuração já apontava para a nova, depois de investigar passo a passo com ajuda de IA. Isso me mostrou que consigo modelar o banco e escrever as regras de acesso, mas ainda não tenho segurança para lidar com portas, variáveis de ambiente e containers. Outra lacuna está no próprio modelo de dados: revisando o diagrama da equipe, percebi que ele não tem como ligar um aluno às turmas em que está matriculado, o que impede a agenda acadêmica, que é justamente o diferencial do produto. Pretendo propor as tabelas de turmas e matrículas na retrospectiva da release e, individualmente, reler as migrations e refazer esses diagnósticos sem ajuda, para conseguir explicar cada decisão com as minhas próprias palavras.