---
title: Jogo de Ações
date: 2026-09-23
description: Simulador de investimentos em bolsa em forma de competição, com dados de mercado reais.
summary: Competições de investimento em que jogadores negociam ações com cotações reais e disputam a melhor evolução de portfólio.
tags: [Java, Spring Boot, Quarkus, AWS, PostgreSQL, BDD]
weight: 10
links:
  - name: Código no GitHub
    url: https://github.com/lalgarve/jogo-acoes
comments: false
ShowReadingTime: false
---

Um jogo de simulação de investimentos em bolsa. Administradores criam competições (públicas
ou privadas), os jogadores entram por um link de login enviado por e-mail e negociam ações com
dados de mercado reais, competindo pela melhor evolução de portfólio.

## O que já funciona

- **Competições públicas e privadas.** Nas públicas, qualquer jogador pode pedir entrada. Nas
  privadas, só entra quem recebeu convite por e-mail.
- **Login sem senha.** O jogador pede o link, recebe por e-mail, clica e está dentro.
- **Validação de e-mail antes do envio.** O sistema confere se o domínio tem registro MX
  válido e não está numa lista de domínios descartáveis.
- **Gestão de jogadores.** O administrador pode reenviar convites e remover jogadores.
- **Captcha auto-hospedado** com ALTCHA (prova de trabalho, sem serviço de terceiros) e
  **log de auditoria**.

## Arquitetura

O sistema principal nunca envia e-mail diretamente: ele publica uma mensagem numa fila, e um
worker assíncrono faz o envio. Assim, o fluxo da aplicação não depende da latência de
terceiros.

- **Sistema principal (Spring Boot).** API REST gerada a partir de uma especificação OpenAPI,
  com persistência JPA/PostgreSQL.
- **Envio de e-mail (Quarkus em AWS Lambda).** Consome a fila Amazon SQS e envia via Amazon
  SES, com suporte a imagem nativa GraalVM.
- **Especificação em BDD.** Cada fluxo tem cenários Gherkin cobrindo o caminho feliz e os
  casos de erro.
- **Integração contínua.** Os testes rodam contra infraestrutura real (Postgres e SQS em
  Docker), com piso de 80% de cobertura de linha (JaCoCo).

## Próximos passos

- Negociação com cotações reais via [Brapi](https://brapi.dev).
- Contabilidade da competição em partida dobrada, com lançamentos *insert-only*.
- Gráficos acessíveis, com descrição textual e sonorização da série; a parte mais pesada será
  em Rust compilado para WebAssembly.
