---
title: "Quarto Envio — 2026-11-18"
authors: [Felipe Duque]
tags: [quarto-envio]
date: 2026-11-18
---

## Pergunta 1 da fase

*Como o feedback recebido (de colegas, professora, monitoria) tem influenciado o que vocês estão fazendo agora?*

No dia 10/11, o Thomas definiu uma regra para a equipe: cada issue tem uma branch e um PR próprios, com um campo de status e o checklist da issue atualizado. Minha parte de banco da Sprint 7 estava em dois PRs grandes, cada um com várias issues. Fechei os dois e dividi o trabalho em oito PRs, um por issue. O efeito apareceu logo: cada PR entrou na dev assim que a API da sua issue ficou pronta. A confirmação de planos entrou no dia 14, a coleta de eventos e o compartilhamento no dia 17, e no dia 18 o Heitor fechou os lembretes em cima da branch em que eu tinha deixado o banco pronto. Com um PR único, nada disso teria entrado antes do resto. Outro feedback veio da CI que o Thomas consertou no dia 11. Ela roda os testes numa cópia do banco feita por `pg_dump` e revelou um defeito meu na exclusão de conta que não aparecia nos meus testes locais. O feedback mais útil desta fase veio de regras e ferramentas que mostraram os problemas cedo. Vou manter o hábito de testar do mesmo jeito que a CI antes de pedir revisão.

## Pergunta 2 da fase

*Conte como tem sido o ritmo de trabalho da sua equipe nesta fase de preparação para a segunda entrega.*

O ritmo ficou desigual. Minha parte de banco da Sprint 8 ficou pronta no dia 11, mas os PRs continuaram em draft esperando a API, enquanto a dev recebia mais de cem commits em quatro dias. No dia 17, ao atualizar os cinco PRs abertos, encontrei conflitos em quase todos. Também havia uma migration do Thomaz com o mesmo número de uma minha (`20261111150000`), e o Supabase recusaria as duas. Além disso, a minha migration de segurança, se entrasse depois das novas, bloquearia a função usada pela página pública de eventos. Renumerei as migrations, liberei a função e rodei os testes de novo. Concluí que trabalho pronto e parado não fica intacto: ele envelhece e precisa ser refeito. Conversei com o Thomas sobre isso, e nos dias seguintes três dessas issues foram concluídas. Daqui para frente, vou atualizar as branches abertas com a dev a cada poucos dias e propor uma regra para a equipe: antes de criar uma migration, conferir os números da dev e dos PRs abertos.

## Pergunta 3 da fase

*Que conhecimentos, ferramentas ou práticas você sente que já domina, e quais ainda são novidade para você neste momento?*

A parte de banco deixou de ser novidade. Escrever migrations, políticas de RLS e testes que conferem se um usuário lê o dado de outro virou rotina. Antes de abrir os PRs, rodei os testes no Supabase local, e os resultados bateram com o esperado: 229 testes no PR de segurança, 209 no de eventos e 215 no de planos. O que ainda é novo está nas bordas do banco: a CI do GitHub Actions, as configurações de CORS e os cabeçalhos de segurança da API. A maior lacuna foi resolver conflitos de merge grandes. Nas duas atualizações das branches, a resolução foi feita com muita ajuda de IA, e o meu papel foi conferir o resultado com os testes. Funcionou, mas mostrou que eu ainda não sei decidir sozinho qual lado de um conflito manter quando ele envolve código de outra pessoa, como no `main.py` e no login. Também quase não mexi no front-end nem no deploy, que ficaram com o Thomas e o Gabriel. Domino a minha camada, mas ainda dependo de ajuda onde ela encontra a dos colegas. Na próxima atualização, vou tentar resolver os conflitos sozinho antes de comparar com a solução sugerida.
