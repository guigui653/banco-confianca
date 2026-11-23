# 🏦 Banco Confiança

Sistema que simula um banco digital, composto por um **aplicativo mobile** e um
**caixa eletrônico (desktop)**. O cliente pode abrir sua conta, depositar, sacar,
transferir e acompanhar seu extrato.

> ⚠️ Projeto para fins de **estudo e portfólio**. Não movimenta dinheiro real.

**Status:** 🚧 Em desenvolvimento (Fase 0: Planejamento)

---

## 🎯 Objetivo

Aprender e praticar os fundamentos de desenvolvimento back-end, banco de dados e
arquitetura de sistemas, construindo um sistema bancário passo a passo: classe por
classe, regra por regra.

---

## ✨ Funcionalidades

### Fase 1: MVP
- [ ] Abrir conta (pessoa física, com CPF)
- [ ] Entrar no aplicativo (login)
- [ ] Entrar no caixa eletrônico (cartão + senha de 6 dígitos)
- [ ] Consultar saldo
- [ ] Depositar (caixa eletrônico)
- [ ] Sacar (caixa eletrônico)
- [ ] Transferir entre contas do Banco Confiança
- [ ] Ver extrato
- [ ] Sair do aplicativo (logout)

### Fase 2: Segurança, PIX e notificações
- [ ] Bloqueio do app ao reabrir (senha, digital ou reconhecimento facial)
- [ ] Senha de transação separada
- [ ] Cadastro de chaves PIX (CPF, e-mail, telefone)
- [ ] Transferência via PIX
- [ ] Notificações em tempo real com o app aberto (WebSocket)
- [ ] Notificações push com o app fechado
- [ ] Alerta de tentativa de acesso suspeita

### Fase 3: Expansão
- [ ] Transferência para outros bancos (simulados)
- [ ] Cartão de crédito
- [ ] Empréstimo
- [ ] Conta para pessoa jurídica (CNPJ)

---

## 🏗️ Arquitetura

```
┌──────────────────┐     ┌──────────────────┐
│   App Mobile     │     │ Caixa Eletrônico │
│  (React Native)  │     │     (React)      │
└────────┬─────────┘     └────────┬─────────┘
         │      HTTP (REST)       │
         └───────────┬────────────┘
                     ▼
         ┌───────────────────────┐        ┌───────────────────────┐
         │   Núcleo do Banco     │◄──────►│  Serviço PIX e        │
         │ (Java + Spring Boot)  │        │  Notificações (Go)    │──► WebSocket / Push
         └───────────┬───────────┘        └───────────────────────┘
                     ▼
              ┌─────────────┐
              │ PostgreSQL  │
              └─────────────┘
```

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| Java + Spring Boot | Núcleo do banco (contas, saldo, transações) |
| Go + Gin | Serviço de PIX e notificações |
| WebSocket | Notificações em tempo real |
| PostgreSQL | Banco de dados |
| React + TypeScript + Vite | Caixa eletrônico (desktop) |
| React Native + Expo | Aplicativo mobile |
| Docker | Ambiente dos serviços e do banco de dados |

---

## 📁 Estrutura do repositório

```
banco-confianca/
├── docs/              # Documentação do projeto
├── backend-java/      # Núcleo do banco (em breve)
├── servico-go/        # PIX e notificações (em breve)
├── caixa-eletronico/  # Front-end do caixa eletrônico (em breve)
├── app-mobile/        # Aplicativo mobile (em breve)
└── docker-compose.yml # Infraestrutura (em breve)
```

---

## 📚 Documentação

- [Visão do produto](docs/visao-do-produto.md)

---

## ▶️ Como executar

_Em breve._

---

## 👤 Autor

**Seu Nome**
[LinkedIn](https://www.linkedin.com/in/seu-perfil) · [GitHub](https://github.com/guigui653)
