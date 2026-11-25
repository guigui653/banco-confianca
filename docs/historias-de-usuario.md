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

## H05: Depositar (caixa eletrônico)
**Como** cliente, **quero** depositar dinheiro em espécie no caixa
eletrônico, **para** aumentar o saldo da minha conta.

**Regras de negócio:**
- **H05-R1:** O valor do depósito deve ser maior que zero.
- **H05-R2:** O depósito aceita apenas cédulas, então o valor deve ser
  em reais inteiros (sem centavos).
- **H05-R3:** O valor máximo por depósito é de R$ 10.000,00.
- **H05-R4:** O saldo é atualizado imediatamente após o depósito.
- **H05-R5:** Todo depósito gera um lançamento no extrato.

---

## H06: Sacar (caixa eletrônico)
**Como** cliente, **quero** sacar dinheiro no caixa eletrônico,
**para** ter dinheiro em espécie.

**Regras de negócio:**
- **H06-R1:** O valor do saque deve ser maior que zero.
- **H06-R2:** O valor do saque deve ser múltiplo de R$ 10,00, pois o
  caixa possui apenas cédulas de R$ 10, R$ 20, R$ 50 e R$ 100.
- **H06-R3:** O valor do saque não pode ser maior que o saldo.
- **H06-R4:** O cliente pode fazer no máximo 3 saques por dia.
- **H06-R5:** O total sacado no dia não pode passar de R$ 5.000,00.
- **H06-R6:** Os limites diários reiniciam à meia-noite.
- **H06-R7:** O caixa eletrônico funciona das 6h às 22h.
- **H06-R8:** O caixa entrega a menor quantidade possível de cédulas,
  começando pela de maior valor.
- **H06-R9:** Se o caixa não tiver cédulas suficientes para montar o
  valor, o saque é recusado e o saldo não é alterado.
- **H06-R10:** Todo saque gera um lançamento no extrato.

---

## H07: Transferir entre contas do Banco Confiança
**Como** cliente, **quero** transferir dinheiro para outra conta do
Banco Confiança, **para** enviar dinheiro a outra pessoa.

**Regras de negócio:**
- **H07-R1:** O valor deve ser maior que zero e pode ter centavos.
- **H07-R2:** O valor não pode ser maior que o saldo.
- **H07-R3:** A conta de destino deve existir.
- **H07-R4:** A conta de destino não pode ser a mesma conta de origem.
- **H07-R5:** Antes de confirmar, o sistema exibe o nome e o CPF
  mascarado do destinatário.
- **H07-R6:** O limite por transferência é de R$ 5.000,00 das 6h às
  20h e de R$ 1.000,00 das 20h às 6h.
- **H07-R7:** A transferência acontece por completo ou não acontece:
  o débito na origem e o crédito no destino ocorrem juntos.
- **H07-R8:** A transferência gera um lançamento no extrato das duas
  contas.

---

## H08: Ver extrato
**Como** cliente, **quero** ver o extrato da minha conta,
**para** acompanhar minhas movimentações.

**Regras de negócio:**
- **H08-R1:** O cliente só pode ver o extrato da própria conta.
- **H08-R2:** Por padrão, o extrato mostra os últimos 30 dias.
- **H08-R3:** O cliente pode filtrar por período (data inicial e final).
- **H08-R4:** Os lançamentos aparecem do mais recente para o mais
  antigo.
- **H08-R5:** Cada lançamento mostra: data e hora, tipo (depósito,
  saque, transferência enviada ou recebida), valor e saldo após a
  operação.
- **H08-R6:** Lançamentos nunca são editados nem apagados. Uma
  correção é feita com um novo lançamento de estorno.

---

## H09: Sair do aplicativo (logout)
**Como** cliente, **quero** sair do aplicativo,
**para** que ninguém acesse minha conta pelo meu celular.

**Regras de negócio:**
- **H09-R1:** Ao sair, a sessão é encerrada e o acesso anterior deixa
  de funcionar.
- **H09-R2:** Para entrar de novo, o cliente deve fazer login novamente.

---

## Regras gerais
- **GER-1:** Valores monetários são sempre tratados com 2 casas
  decimais, sem erros de arredondamento.
- **GER-2:** Todas as datas e horas seguem o horário de Brasília.