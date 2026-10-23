---
title: "Posso Desenvolver Software com IA sem ser Programador?"
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
comments: true
---

A promessa que IA pode democratizar o desenvolvimento de software é verdadeira em parte. Essa promessa nem é nova, já se prevê o fim dos programadores a décadas.  O artigo em inglês  [The Eternal Promise: Will AI Replace Developers? A 60-Year History (2026)](https://modelslab.com/blog/api/will-ai-replace-developers-eternal-promise-2026) listas as promessas começando em 1959.

Em 1959 foi especificada a linguagem COBOL e os primeiros compiladores em 1960. O objetivo declarado do COBOL era criar uma linguagem de programação próxima do inglês. Assim, gerentes de negócios poderiam ler, entender e, quem sabe, escrever nela.

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







