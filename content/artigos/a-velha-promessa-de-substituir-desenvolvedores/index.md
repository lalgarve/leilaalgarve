---
title: "A velha promessa de substituir desenvolvedores"
date: 2026-10-21T21:11:45-03:00
draft: true
description: ""
summary: ""
tags: []
categories: []
cover:
  image: ""   # ex.: cover.jpg dentro da pasta do artigo
  alt: ""
  hidden: false
series: [IA não substituirá desenvolvedores] 
series_weight: 10 
comments: true
---

Com o advento da IA, surgiu a promessa IA pode democratizar o desenvolvimento de software. Essa promessa nem é nova, já se prevê o fim dos programadores a décadas.  O artigo em inglês  [The Eternal Promise: Will AI Replace Developers? A 60-Year History (2026)](https://modelslab.com/blog/api/will-ai-replace-developers-eternal-promise-2026) listas as promessas começando em 1959.

## COBOL

Em 1959 foi especificada a linguagem COBOL e os primeiros compiladores em 1960. O objetivo declarado do COBOL era criar uma linguagem de programação próxima do inglês. Assim, gerentes de negócios poderiam ler, entender e, quem sabe, escrever nela.

O código COBOL abaixo multiplica um valor por 0,15. VALOR é inicializado com 200 (linha 5), RESULTADO é declarado na linha 6 e na linha 8 é feita a multiplicação depois o programa imprime o resultado.

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. CALCULA-PERCENTUAL.
       DATA DIVISION.
       WORKING-STORAGE SECTION.
       01 VALOR       PIC 9(7)V99 VALUE 200.00.
       01 RESULTADO   PIC ZZZZZZ9.99.
       PROCEDURE DIVISION.
           MULTIPLY VALOR BY 0.15 GIVING RESULTADO.
           DISPLAY "RESULTADO: " RESULTADO.
           STOP RUN.
```

Para entender a revolução, precisamos comparar como programas eram escritos antes usando Assembly. O Assembly permite reservar espaço na memória para variáveis. Ou seja, inclui um gerenciamento de memória mínimo. Nem isso existia para os primeiros computadores.

No código abaixo, valor e resultado são declarados nas linhas 2 e 5. A multiplicação acontece da linha 10 até 16. Precisamos de 7 linhas para multiplicar um número por uma constante. O programa também *não imprime* o resultado. 

```nasm
section .data
    valor      dq 20000        ; R$ 200,00 em centavos

section .bss
    resultado  resq 1

section .text
    global _start
_start:
    mov  rax, [valor]          ; carrega o valor
    mov  rbx, 15
    mul  rbx                   ; rax = valor * 15
    mov  rbx, 100
    xor  rdx, rdx
    div  rbx                   ; rax = (valor * 15) / 100
    mov  [resultado], rax      ; guarda o resultado: 3000 centavos
    mov  rax, 60               ; encerra o programa
    xor  rdi, rdi
    syscall
```
Em COBOL o comando _DISPLAY_ mostra algo na tela. Pode ser em um programa rodando em um Mainframe ou em um PC. Já o Assembly não tem algo equivalente. Pode ser que para mostrar os dados se precise modificar um local específico da memória. Ou seja, COBOL abstrai o conceito de como mostrar os dados. 

