# Banco Confiança: Visão do Produto

## O que é
O Banco Confiança é um sistema que simula um banco digital. Ele é composto
por um aplicativo mobile e um caixa eletrônico (desktop), onde o cliente pode
abrir sua conta, depositar, sacar, transferir e acompanhar seu extrato.

O projeto foi criado para fins de estudo e portfólio, com foco em aprender
os fundamentos de back-end, banco de dados e arquitetura de sistemas.

## Quem usa
- **Cliente (no aplicativo):** abre a conta, consulta saldo e extrato,
  faz transferências.
- **Cliente (no caixa eletrônico):** acessa com cartão e senha de 6 dígitos
  para sacar, depositar e consultar saldo.
- **Administrador do banco (futuro):** gerencia contas e o caixa eletrônico.

## Funcionalidades do MVP
- Abrir conta (pessoa física, com CPF)
- Entrar no aplicativo (login)
- Entrar no caixa eletrônico (cartão + senha de 6 dígitos)
- Consultar saldo
- Depositar (caixa eletrônico)
- Sacar (caixa eletrônico)
- Transferir entre contas do Banco Confiança
- Ver extrato
- Sair do aplicativo (logout)

## Próximas fases
- **Fase 2:** bloqueio do app ao reabrir (senha, digital ou rosto), senha de
  transação, chaves PIX, PIX, notificações em tempo real (WebSocket) e push,
  alerta de acesso suspeito.
- **Fase 3:** transferência para outros bancos (simulados), cartão de
  crédito, empréstimo e conta para pessoa jurídica (CNPJ).

## O que o sistema NÃO faz
- Não movimenta dinheiro real.
- Não se conecta ao Banco Central nem a bancos reais.
- Não usa hardware real de caixa eletrônico (leitor de cartão, dispensador
  de notas): esses recursos são simulados.

## Tecnologias
| Tecnologia | Uso | Por quê |
|---|---|---|
| Java + Spring Boot | Núcleo do banco | Linguagem muito usada no setor bancário. |
| Go + Gin | PIX e notificações | Leve e eficiente com muitas conexões simultâneas. |
| WebSocket | Notificações com o app aberto | O servidor avisa o app sem que o app pergunte. |
| Notificações push (Expo) | Notificações com o app fechado | O WebSocket só funciona com o app aberto. |
| PostgreSQL | Banco de dados | Confiável e com suporte a transações seguras. |
| React + TypeScript + Vite | Caixa eletrônico | _(escreva aqui)_ |
| React Native + Expo | Aplicativo mobile | Reaproveita o conhecimento de React. |
| Docker | Ambiente dos serviços | Mesmo ambiente em qualquer máquina. |
