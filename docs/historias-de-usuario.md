# Banco Confiança: Histórias de Usuário

> Cada regra tem um código (ex.: H02-R3) para ser referenciada
> no código, nos testes e nos cards do Kanban.

---

## H01: Abrir conta
**Como** pessoa física, **quero** abrir uma conta informando meus dados,
**para** começar a usar o banco.

**Dados obrigatórios:** nome completo, CPF, data de nascimento, e-mail,
telefone, senha do app e senha do cartão.

**Regras de negócio:**
- **H01-R1:** O CPF deve ser válido (cálculo dos dígitos verificadores).
- **H01-R2:** Não pode existir mais de uma conta com o mesmo CPF.
- **H01-R3:** Não pode existir mais de uma conta com o mesmo e-mail.
- **H01-R4:** O cliente deve ter 18 anos ou mais.
- **H01-R5:** A senha do app deve ter no mínimo 8 caracteres, com pelo
  menos 1 letra e 1 número.
- **H01-R6:** A senha do cartão deve ter exatamente 6 dígitos numéricos.
- **H01-R7:** A senha do cartão não pode ser uma sequência (123456),
  ter todos os dígitos iguais (111111) nem ser a data de nascimento.
- **H01-R8:** A senha do app e a senha do cartão devem ser diferentes.
- **H01-R9:** A conta começa com saldo de R$ 0,00.
- **H01-R10:** Ao abrir a conta, é gerado automaticamente um cartão
  com número de 16 dígitos.

---

## H02: Entrar no aplicativo (login)
**Como** cliente, **quero** entrar no aplicativo com meus dados,
**para** acessar minha conta.

**Regras de negócio:**
- **H02-R1:** O cliente pode entrar usando o CPF **ou** o e-mail, junto
  com a senha do app.
- **H02-R2:** Em caso de erro, a mensagem é sempre genérica:
  "CPF/e-mail ou senha inválidos". O sistema nunca informa qual dos
  dois está errado.
- **H02-R3:** Após 3 tentativas erradas seguidas, o acesso é bloqueado
  por 15 minutos.
- **H02-R4:** Durante o bloqueio, o cliente pode desbloquear o acesso
  com um código de 6 dígitos enviado para o e-mail cadastrado.
- **H02-R5:** O código de desbloqueio expira em 10 minutos.
- **H02-R6:** Um login com sucesso zera o contador de tentativas erradas.

---

## H03: Entrar no caixa eletrônico
**Como** cliente, **quero** acessar o caixa eletrônico com meu cartão
e senha, **para** fazer saques, depósitos e consultas.

**Regras de negócio:**
- **H03-R1:** O acesso é feito com o número do cartão (16 dígitos) e a
  senha do cartão (6 dígitos). Digitar o número simula inserir o cartão.
- **H03-R2:** Após 3 tentativas erradas seguidas, o cartão é bloqueado.
- **H03-R3:** O cartão bloqueado só pode ser desbloqueado pelo
  aplicativo, com um código enviado para o e-mail cadastrado.
- **H03-R4:** Após 60 segundos sem nenhuma ação, a sessão é encerrada
  e o caixa volta para a tela inicial.
- **H03-R5:** Ao finalizar a operação, a sessão é encerrada e o caixa
  volta para a tela inicial.

---

## H04: Consultar saldo
**Como** cliente, **quero** consultar meu saldo,
**para** saber quanto dinheiro tenho disponível.

**Regras de negócio:**
- **H04-R1:** O cliente só pode consultar o saldo da própria conta.
- **H04-R2:** O saldo nunca pode ficar negativo (não há cheque especial
  no MVP).
- **H04-R3:** O saldo é exibido no formato brasileiro: R$ 1.234,56.

---

## Requisitos gerais de segurança e privacidade (LGPD)
- **SEG-1:** Senhas nunca são armazenadas em texto puro, apenas como
  hash.
- **SEG-2:** O CPF é exibido mascarado nas telas: ***.456.789-**.
- **SEG-3:** Dados de um cliente nunca são exibidos para outro cliente.

---

_Parte 2 (H05 a H09) em construção._