### UC01 — Realizar Login

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Usuário (Aluno, Recepcionista, Instrutor, Gerente) |
| **Objetivo** | Permitir que o usuário acesse o sistema com autenticação segura. |

**Pré-condições**
- Usuário deve possuir cadastro ativo no sistema.

**Pós-condições**
- Sessão iniciada com sucesso e usuário redirecionado à tela inicial conforme seu perfil.

**Fluxo Principal**
1. O usuário acessa a tela de login.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais.
4. O sistema autentica o usuário.
5. O sistema redireciona o usuário para a tela inicial de acordo com o perfil (RN06).

**Fluxos Alternativos**
- **A1 — Senha incorreta:** O sistema exibe mensagem de erro e solicita nova tentativa.
- **A2 — Conta bloqueada:** O sistema impede o login e orienta o usuário a recuperar o acesso.
- **A3 — Usuário não encontrado:** O sistema exibe mensagem informando que o cadastro não existe.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| _(pré-requisito geral)_ | RNF02, RNF03, RNF04 | RN06 |


### DA01 — Realizar Login (UC01)

```plantuml
@startuml DA01_RealizarLogin
title DA01 — Realizar Login

start
:Usuário acessa a tela de login;
:Informa e-mail e senha;
:Sistema valida as credenciais;

if (Credenciais válidas?) then (Não)
  if (Conta bloqueada?) then (Sim)
    :Exibe mensagem de conta bloqueada;
    :Orienta recuperação de acesso;
    stop
  else (Não)
    :Exibe mensagem de erro;
    :Solicita nova tentativa;
    stop
  endif
else (Sim)
  :Autentica o usuário;
  :Redireciona para tela inicial conforme perfil (RN06);
  stop
endif

@enduml
```

---

### UC02 — Cadastrar Aluno

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Recepcionista |
| **Objetivo** | Registrar um novo aluno no sistema com todos os dados necessários para matrícula. |

**Pré-condições**
- Recepcionista autenticado no sistema.
- Plano a ser contratado deve existir e estar ativo (RF02).

**Pós-condições**
- Aluno cadastrado e com matrícula ativa no sistema.
- Cartão RFID vinculado ao aluno.

**Fluxo Principal**
1. O recepcionista acessa o módulo de matrículas.
2. O recepcionista preenche os dados pessoais do aluno (nome, CPF, data de nascimento, contato, endereço).
3. O recepcionista seleciona o plano a ser contratado.
4. O sistema valida os dados informados.
5. O sistema registra o aluno e gera um código de matrícula.
6. O sistema vincula o cartão RFID ao aluno.
7. O sistema confirma o cadastro.

**Fluxos Alternativos**
- **A1 — CPF já cadastrado:** O sistema alerta que o CPF já existe e exibe os dados do aluno existente.
- **A2 — Dados inválidos:** O sistema exibe mensagem de erro indicando os campos inválidos.
- **A3 — Plano indisponível:** O sistema exibe apenas os planos ativos para seleção.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF01, RF02, RF05 | RNF02, RNF04 | RN06 |


### DA02 — Cadastrar Aluno (UC02)

```plantuml
@startuml DA02_CadastrarAluno
title DA02 — Cadastrar Aluno

start
:Recepcionista acessa o módulo de matrículas;
:Preenche dados pessoais do aluno;
:Seleciona o plano a ser contratado;
:Sistema valida os dados;

if (CPF já cadastrado?) then (Sim)
  :Exibe alerta com dados do aluno existente;
  stop
else (Não)
  if (Dados válidos?) then (Não)
    :Exibe campos inválidos;
    stop
  else (Sim)
    if (Plano disponível?) then (Não)
      :Exibe somente planos ativos;
      stop
    else (Sim)
      :Registra aluno e gera código de matrícula;
      :Vincula cartão RFID ao aluno;
      :Confirma cadastro;
      stop
    endif
  endif
endif

@enduml
```

---

### UC03 — Gerenciar Planos

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Criar, editar, ativar e desativar planos oferecidos pela academia. |

**Pré-condições**
- Gerente autenticado no sistema.

**Pós-condições**
- Plano criado, editado, ativado ou desativado conforme ação realizada.

**Fluxo Principal**
1. O gerente acessa o módulo de planos.
2. O gerente seleciona a ação desejada: criar, editar, ativar ou desativar.
3. Para criar: o gerente preenche nome, tipo, valor e modalidades inclusas.
4. O sistema valida os dados.
5. O sistema salva as alterações e confirma a operação.

**Fluxos Alternativos**
- **A1 — Plano com nome duplicado:** O sistema alerta que já existe um plano com o mesmo nome.
- **A2 — Desativar plano com alunos ativos:** O sistema exibe aviso sobre a quantidade de alunos afetados e solicita confirmação.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF02 | RNF04, RNF05 | RN06 |


### DA03 — Gerenciar Planos (UC03)

```plantuml
@startuml DA03_GerenciarPlanos
title DA03 — Gerenciar Planos

start
:Gerente acessa módulo de planos;
:Seleciona ação (Criar / Editar / Ativar / Desativar);

if (Ação = Criar?) then (Sim)
  :Preenche nome, tipo, valor e modalidades;
  if (Nome duplicado?) then (Sim)
    :Exibe alerta de nome duplicado;
    stop
  else (Não)
    :Salva novo plano;
  endif
elseif (Ação = Desativar?) then (Sim)
  if (Alunos ativos no plano?) then (Sim)
    :Exibe aviso com quantidade de alunos afetados;
    if (Gerente confirma?) then (Não)
      stop
    else (Sim)
      :Desativa o plano;
    endif
  else (Não)
    :Desativa o plano;
  endif
else (Editar / Ativar)
  :Atualiza dados do plano;
endif

:Confirma operação;
stop

@enduml
```

---

### UC04 — Registrar Pagamento

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Recepcionista |
| **Objetivo** | Registrar o pagamento da mensalidade de um aluno e atualizar sua situação de regularidade. |

**Pré-condições**
- Recepcionista autenticado no sistema.
- Aluno deve estar cadastrado.

**Pós-condições**
- Pagamento registrado.
- Situação do aluno atualizada para "regular" automaticamente.

**Fluxo Principal**
1. O recepcionista acessa o módulo de pagamentos.
2. O recepcionista busca o aluno pelo nome ou CPF.
3. O sistema exibe a mensalidade em aberto.
4. O recepcionista seleciona a forma de pagamento (dinheiro, cartão ou PIX).
5. O sistema registra o pagamento integral.
6. O sistema atualiza automaticamente a situação do aluno para regular (RN07).
7. O sistema emite comprovante de pagamento.

**Fluxos Alternativos**
- **A1 — Aluno não encontrado:** O sistema exibe mensagem de erro e solicita nova busca.
- **A2 — Tentativa de pagamento parcial:** O sistema bloqueia a operação e informa que pagamentos parciais não são permitidos (RN04).
- **A3 — Pagamento online (boleto/cartão):** O sistema gera boleto ou link de pagamento e envia ao aluno.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF03, RF04, RF10 | RNF02, RNF03 | RN04, RN07 |


### DA04 — Registrar Pagamento (UC04)

```plantuml
@startuml DA04_RegistrarPagamento
title DA04 — Registrar Pagamento

start
:Recepcionista acessa módulo de pagamentos;
:Busca aluno por nome ou CPF;

if (Aluno encontrado?) then (Não)
  :Exibe mensagem de erro;
  stop
else (Sim)
  :Sistema exibe mensalidade em aberto;
  :Seleciona forma de pagamento (Dinheiro / Cartão / PIX / Online);

  if (Pagamento parcial?) then (Sim)
    :Bloqueia operação — RN04;
    stop
  else (Não)
    if (Pagamento online?) then (Sim)
      :Gera boleto ou link e envia ao aluno;
    else (Presencial)
      :Registra pagamento integral;
    endif
    :Atualiza situação do aluno para Regular — RN07;
    :Emite comprovante de pagamento;
    stop
  endif
endif

@enduml
```

---

### UC05 — Verificar Regularidade do Aluno

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Sistema (automático) / Recepcionista |
| **Objetivo** | Verificar se o aluno está com a mensalidade em dia antes de liberar acesso ou serviços. |

**Pré-condições**
- Aluno deve estar cadastrado no sistema.

**Pós-condições**
- Situação do aluno exibida (regular ou inadimplente).

**Fluxo Principal**
1. O sistema recebe solicitação de verificação (via catraca, recepcionista ou agendamento).
2. O sistema consulta a data de vencimento da mensalidade do aluno.
3. O sistema verifica se o pagamento está em dia.
4. O sistema retorna o status: "Regular" ou "Inadimplente".

**Fluxos Alternativos**
- **A1 — Aluno inadimplente há mais de 5 dias:** O sistema bloqueia o acesso e notifica o aluno sobre a pendência (RN01).
- **A2 — Aluno com vencimento próximo:** O sistema envia notificação prévia ao aluno (RF10).

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF04, RF10 | RNF01, RNF03 | RN01, RN07 |


### DA05 — Verificar Regularidade do Aluno (UC05)

```plantuml
@startuml DA05_VerificarRegularidade
title DA05 — Verificar Regularidade do Aluno

start
:Sistema recebe solicitação de verificação;
:Consulta data de vencimento da mensalidade;

if (Pagamento em dia?) then (Sim)
  :Retorna status: REGULAR;
  stop
else (Não)
  if (Inadimplente há mais de 5 dias? — RN01) then (Sim)
    :Bloqueia acesso/serviço;
    :Notifica o aluno sobre a pendência;
    stop
  else (Não — vencimento próximo)
    :Retorna status: INADIMPLENTE;
    :Envia notificação preventiva — RF10;
    stop
  endif
endif

@enduml
```

---

### UC06 — Controlar Acesso pela Catraca (RFID)

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Sistema de Catraca (API Externa) / Aluno |
| **Objetivo** | Validar a entrada do aluno na academia por meio do cartão RFID integrado à catraca. |

**Pré-condições**
- Aluno possui cartão RFID ativo vinculado ao seu cadastro.
- Sistema de catraca integrado via API REST.

**Pós-condições**
- Acesso liberado ou negado registrado no histórico.
- Log de entrada criado.

**Fluxo Principal**
1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia o código RFID ao sistema via API REST (RNF06).
3. O sistema identifica o aluno pelo RFID.
4. O sistema verifica a regularidade do aluno (UC05).
5. O sistema retorna autorização para a catraca.
6. A catraca libera a entrada.
7. O sistema registra o acesso no histórico.

**Fluxos Alternativos**
- **A1 — Aluno inadimplente:** O sistema retorna negativa; a catraca bloqueia a entrada e exibe mensagem de alerta.
- **A2 — RFID não reconhecido:** O sistema retorna erro; catraca bloqueia e solicita atendimento na recepção.
- **A3 — Falha na comunicação com a API:** A catraca registra a tentativa e pode operar em modo offline temporário.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF05, RF04 | RNF01, RNF03, RNF06 | RN01 |


### DA06 — Controlar Acesso pela Catraca (UC06)

```plantuml
@startuml DA06_ControlarAcessoCatraca
title DA06 — Controlar Acesso pela Catraca (RFID)

start
:Aluno aproxima cartão RFID da catraca;
:Catraca envia código RFID ao sistema via API REST — RNF06;

if (Comunicação com API OK?) then (Não)
  :Catraca registra tentativa em modo offline;
  stop
else (Sim)
  if (RFID reconhecido?) then (Não)
    :Sistema retorna erro;
    :Catraca bloqueia e solicita atendimento na recepção;
    stop
  else (Sim)
    :Sistema identifica o aluno;
    :Verifica regularidade do aluno — UC05;

    if (Aluno Regular?) then (Sim)
      :Sistema autoriza entrada;
      :Catraca libera a passagem;
      :Sistema registra acesso no histórico;
      stop
    else (Não — Inadimplente)
      :Sistema retorna negativa;
      :Catraca bloqueia a entrada;
      :Exibe mensagem de alerta ao aluno;
      stop
    endif
  endif
endif

@enduml
```

---

### UC07 — Agendar Aula

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Aluno |
| **Objetivo** | Permitir que o aluno visualize os horários disponíveis e reserve uma vaga em uma aula. |

**Pré-condições**
- Aluno autenticado e com situação regular.
- Existir aulas disponíveis com vagas.

**Pós-condições**
- Reserva confirmada e vaga deduzida do total disponível.
- Notificação de confirmação enviada ao aluno.

**Fluxo Principal**
1. O aluno acessa o módulo de agendamento.
2. O sistema exibe as aulas disponíveis com horários e vagas restantes.
3. O aluno seleciona a aula desejada.
4. O sistema verifica disponibilidade de vagas (RN02).
5. O sistema confirma o agendamento.
6. O sistema envia notificação de confirmação ao aluno (RF10).

**Fluxos Alternativos**
- **A1 — Aula sem vagas:** O sistema bloqueia o agendamento e informa que a aula está lotada (RN02).
- **A2 — Aluno inadimplente:** O sistema bloqueia o agendamento e redireciona para regularização.
- **A3 — Aula já agendada pelo aluno:** O sistema informa que o aluno já possui reserva nesse horário.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF06, RF04, RF10 | RNF03, RNF04 | RN01, RN02 |


### DA07 — Agendar Aula (UC07)

```plantuml
@startuml DA07_AgendarAula
title DA07 — Agendar Aula

start
:Aluno acessa módulo de agendamento;
:Sistema verifica regularidade do aluno — UC05;

if (Aluno regular?) then (Não)
  :Bloqueia agendamento;
  :Redireciona para regularização;
  stop
else (Sim)
  :Sistema exibe aulas disponíveis com horários e vagas;
  :Aluno seleciona a aula desejada;

  if (Aula já agendada pelo aluno?) then (Sim)
    :Informa duplicidade de reserva;
    stop
  else (Não)
    if (Vagas disponíveis? — RN02) then (Não)
      :Informa aula lotada;
      stop
    else (Sim)
      :Confirma agendamento;
      :Deduz vaga do total disponível;
      :Envia notificação de confirmação — UC16;
      stop
    endif
  endif
endif

@enduml
```

---

### UC08 — Cancelar Agendamento

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Aluno |
| **Objetivo** | Permitir que o aluno cancele uma reserva de aula previamente realizada. |

**Pré-condições**
- Aluno autenticado.
- Aluno possui reserva ativa para a aula.
- Cancelamento realizado com pelo menos 1 hora de antecedência (RN03).

**Pós-condições**
- Reserva cancelada e vaga devolvida ao total disponível.

**Fluxo Principal**
1. O aluno acessa o módulo de agendamentos.
2. O aluno visualiza suas reservas ativas.
3. O aluno seleciona a aula que deseja cancelar.
4. O sistema verifica se o cancelamento está dentro do prazo permitido (RN03).
5. O sistema cancela a reserva.
6. O sistema devolve a vaga para a aula.
7. O sistema confirma o cancelamento ao aluno.

**Fluxos Alternativos**
- **A1 — Cancelamento fora do prazo:** O sistema bloqueia o cancelamento e informa que o prazo de 1 hora já passou (RN03).
- **A2 — Aula já encerrada:** O sistema informa que não é possível cancelar uma aula já realizada.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF06 | RNF03, RNF04 | RN03 |


### DA08 — Cancelar Agendamento (UC08)

```plantuml
@startuml DA08_CancelarAgendamento
title DA08 — Cancelar Agendamento

start
:Aluno acessa módulo de agendamentos;
:Sistema exibe reservas ativas do aluno;
:Aluno seleciona aula que deseja cancelar;

if (Aula já encerrada?) then (Sim)
  :Informa impossibilidade de cancelamento;
  stop
else (Não)
  if (Antecedência mínima de 1h? — RN03) then (Não)
    :Bloqueia cancelamento — prazo expirado;
    stop
  else (Sim)
    :Cancela a reserva;
    :Devolve vaga para a aula;
    :Confirma cancelamento ao aluno;
    stop
  endif
endif

@enduml
```

---

### UC09 — Registrar Presença em Aula

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Instrutor |
| **Objetivo** | Registrar a presença dos alunos em uma aula ministrada. |

**Pré-condições**
- Instrutor autenticado no sistema.
- Aula em andamento ou recém-encerrada.
- Alunos com reserva confirmada para a aula.

**Pós-condições**
- Presença dos alunos registrada no histórico da aula.

**Fluxo Principal**
1. O instrutor acessa o módulo de lista de presença.
2. O sistema exibe a lista de alunos com reserva na aula atual.
3. O instrutor marca os alunos presentes.
4. O sistema salva o registro de presença.
5. O sistema confirma o registro ao instrutor.

**Fluxos Alternativos**
- **A1 — Aluno sem reserva comparecer:** O instrutor pode registrar presença avulsa, se houver vaga disponível.
- **A2 — Falha ao salvar:** O sistema exibe mensagem de erro e solicita nova tentativa.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF07 | RNF01, RNF04 | RN06 |


### DA09 — Registrar Presença em Aula (UC09)

```plantuml
@startuml DA09_RegistrarPresenca
title DA09 — Registrar Presença em Aula

start
:Instrutor acessa módulo de lista de presença;
:Sistema exibe alunos com reserva na aula atual;
:Instrutor marca alunos presentes;

if (Aluno sem reserva presente?) then (Sim)
  if (Há vaga disponível?) then (Sim)
    :Registra presença avulsa;
  else (Não)
    :Informa ausência de vaga para presença avulsa;
  endif
else (Não)
  :Salva registros de presença;
endif

if (Falha ao salvar?) then (Sim)
  :Exibe mensagem de erro;
  :Solicita nova tentativa;
  stop
else (Não)
  :Confirma registro ao instrutor;
  stop
endif

@enduml
```

---

### UC10 — Realizar Avaliação Física

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Instrutor |
| **Objetivo** | Registrar os dados da avaliação física de um aluno (peso, IMC, percentual de gordura etc.). |

**Pré-condições**
- Instrutor autenticado no sistema.
- Aluno ativo e regular no sistema (RN05).

**Pós-condições**
- Avaliação física salva no histórico do aluno.
- Notificação enviada ao aluno informando a disponibilidade da avaliação (RF10).

**Fluxo Principal**
1. O instrutor acessa o módulo de avaliações físicas.
2. O instrutor busca o aluno pelo nome ou matrícula.
3. O sistema verifica se o aluno está ativo e regular (RN05).
4. O instrutor preenche os dados da avaliação (peso, altura, IMC, % de gordura, etc.).
5. O instrutor pode anexar arquivos complementares.
6. O sistema salva a avaliação.
7. O sistema notifica o aluno sobre a nova avaliação disponível (RF10).

**Fluxos Alternativos**
- **A1 — Aluno inadimplente:** O sistema bloqueia a realização da avaliação e informa o motivo (RN05).
- **A2 — Aluno inativo:** O sistema bloqueia a avaliação e exibe o status do aluno.
- **A3 — Erro no upload de arquivo:** O sistema exibe mensagem de erro e solicita novo envio.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF08, RF04, RF10 | RNF02, RNF04 | RN05, RN06 |


### DA10 — Realizar Avaliação Física (UC10)

```plantuml
@startuml DA10_RealizarAvaliacaoFisica
title DA10 — Realizar Avaliação Física

start
:Instrutor acessa módulo de avaliações físicas;
:Busca aluno por nome ou matrícula;
:Sistema verifica se aluno está ativo e regular — RN05;

if (Aluno ativo e regular?) then (Não)
  :Bloqueia avaliação;
  :Exibe motivo (inadimplente ou inativo);
  stop
else (Sim)
  :Instrutor preenche dados da avaliação (peso, IMC, % gordura etc.);
  
  if (Deseja anexar arquivo?) then (Sim)
    :Faz upload do arquivo;
    if (Upload com erro?) then (Sim)
      :Exibe mensagem de erro;
      :Solicita novo envio;
    else (Não)
      :Arquivo anexado com sucesso;
    endif
  else (Não)
  endif

  :Sistema salva a avaliação;
  :Sistema notifica o aluno — UC17;
  stop
endif

@enduml
```

---

### UC11 — Emitir Relatório de Inadimplência

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Gerar relatório com a lista de alunos inadimplentes para análise e tomada de decisão. |

**Pré-condições**
- Gerente autenticado no sistema.

**Pós-condições**
- Relatório de inadimplência gerado e disponível para visualização ou download.

**Fluxo Principal**
1. O gerente acessa o módulo de relatórios gerenciais.
2. O gerente seleciona "Relatório de Inadimplência".
3. O gerente define filtros opcionais (período, plano, unidade).
4. O sistema processa os dados e gera o relatório.
5. O sistema exibe o relatório com nome, CPF, plano, valor e dias em atraso.
6. O gerente pode exportar o relatório em PDF ou planilha.

**Fluxos Alternativos**
- **A1 — Nenhum inadimplente no período:** O sistema exibe mensagem informando que não há registros para o filtro aplicado.
- **A2 — Erro na geração:** O sistema exibe mensagem de erro e registra log.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF09, RF04 | RNF03, RNF05 | RN01, RN06 |


### DA11 — Emitir Relatório de Inadimplência (UC11)

```plantuml
@startuml DA11_RelatorioInadimplencia
title DA11 — Emitir Relatório de Inadimplência

start
:Gerente acessa módulo de relatórios gerenciais;
:Seleciona "Relatório de Inadimplência";
:Define filtros opcionais (período, plano, unidade);
:Sistema processa os dados;

if (Erro na geração?) then (Sim)
  :Exibe mensagem de erro e registra log;
  stop
else (Não)
  if (Há inadimplentes no período?) then (Não)
    :Informa ausência de registros;
    stop
  else (Sim)
    :Exibe relatório (nome, CPF, plano, valor, dias em atraso);
    if (Deseja exportar?) then (Sim)
      :Exporta relatório em PDF ou planilha;
    else (Não)
    endif
    stop
  endif
endif

@enduml
```

---

### UC12 — Emitir Relatório de Alunos Ativos

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Gerar relatório com a lista de alunos ativos na academia. |

**Pré-condições**
- Gerente autenticado no sistema.

**Pós-condições**
- Relatório de alunos ativos gerado e disponível.

**Fluxo Principal**
1. O gerente acessa o módulo de relatórios gerenciais.
2. O gerente seleciona "Relatório de Alunos Ativos".
3. O gerente define filtros opcionais (plano, período, modalidade).
4. O sistema processa e gera o relatório.
5. O sistema exibe nome, matrícula, plano e data de vencimento de cada aluno.
6. O gerente pode exportar o relatório.

**Fluxos Alternativos**
- **A1 — Nenhum aluno ativo no filtro:** O sistema informa que não há registros para os critérios selecionados.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF09 | RNF03, RNF05 | RN06 |


### DA12 — Emitir Relatório de Alunos Ativos (UC12)

```plantuml
@startuml DA12_RelatorioAlunosAtivos
title DA12 — Emitir Relatório de Alunos Ativos

start
:Gerente acessa módulo de relatórios gerenciais;
:Seleciona "Relatório de Alunos Ativos";
:Define filtros opcionais (plano, período, modalidade);
:Sistema processa e gera o relatório;

if (Alunos encontrados?) then (Não)
  :Informa ausência de registros para o filtro;
  stop
else (Sim)
  :Exibe nome, matrícula, plano e data de vencimento;
  if (Deseja exportar?) then (Sim)
    :Exporta relatório;
  else (Não)
  endif
  stop
endif

@enduml
```

---

### UC13 — Emitir Relatório de Histórico de Acessos

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Gerar relatório com o histórico de entradas dos alunos na academia registradas via catraca. |

**Pré-condições**
- Gerente autenticado no sistema.

**Pós-condições**
- Relatório de acessos gerado e disponível.

**Fluxo Principal**
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona "Histórico de Acessos".
3. O gerente define filtros (aluno, período, unidade).
4. O sistema consulta os logs da catraca e gera o relatório.
5. O sistema exibe data, hora e resultado (liberado/negado) de cada acesso.
6. O gerente pode exportar o relatório.

**Fluxos Alternativos**
- **A1 — Nenhum acesso no período:** O sistema informa que não há registros para o filtro selecionado.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF09, RF05 | RNF03, RNF05 | RN06 |


### DA13 — Emitir Relatório de Histórico de Acessos (UC13)

```plantuml
@startuml DA13_RelatorioHistoricoAcessos
title DA13 — Emitir Relatório de Histórico de Acessos

start
:Gerente acessa módulo de relatórios;
:Seleciona "Histórico de Acessos";
:Define filtros (aluno, período, unidade);
:Sistema consulta logs da catraca;

if (Registros encontrados?) then (Não)
  :Informa ausência de registros para o filtro;
  stop
else (Sim)
  :Exibe data, hora e resultado (liberado/negado) de cada acesso;
  if (Deseja exportar?) then (Sim)
    :Exporta relatório;
  else (Não)
  endif
  stop
endif

@enduml
```

---

### UC14 — Emitir Relatório de Ocupação das Aulas

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Gerente |
| **Objetivo** | Gerar relatório com dados de ocupação e frequência das aulas oferecidas. |

**Pré-condições**
- Gerente autenticado no sistema.

**Pós-condições**
- Relatório de ocupação gerado e disponível.

**Fluxo Principal**
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona "Ocupação das Aulas".
3. O gerente define filtros (modalidade, instrutor, período).
4. O sistema processa os dados de agendamentos e presenças.
5. O sistema exibe taxa de ocupação, número de alunos e capacidade por aula.
6. O gerente pode exportar o relatório.

**Fluxos Alternativos**
- **A1 — Nenhuma aula no período:** O sistema informa ausência de registros.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF09, RF06, RF07 | RNF03, RNF05 | RN02, RN06 |


### DA14 — Emitir Relatório de Ocupação das Aulas (UC14)

```plantuml
@startuml DA14_RelatorioOcupacaoAulas
title DA14 — Emitir Relatório de Ocupação das Aulas

start
:Gerente acessa módulo de relatórios;
:Seleciona "Ocupação das Aulas";
:Define filtros (modalidade, instrutor, período);
:Sistema processa dados de agendamentos e presenças;

if (Há aulas no período?) then (Não)
  :Informa ausência de registros;
  stop
else (Sim)
  :Exibe taxa de ocupação, número de alunos e capacidade por aula;
  if (Deseja exportar?) then (Sim)
    :Exporta relatório;
  else (Não)
  endif
  stop
endif

@enduml
```

---

### UC15 — Enviar Notificação de Vencimento de Mensalidade

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Sistema (automático) |
| **Objetivo** | Notificar o aluno sobre o próximo vencimento da mensalidade para evitar inadimplência. |

**Pré-condições**
- Aluno cadastrado com e-mail ou telefone válido.
- Mensalidade próxima ao vencimento (ex.: 5 dias antes).

**Pós-condições**
- Notificação enviada e registrada no histórico de comunicações.

**Fluxo Principal**
1. O sistema executa rotina automática diária.
2. O sistema identifica alunos com vencimento próximo.
3. O sistema gera a mensagem de notificação personalizada.
4. O sistema envia a notificação por e-mail e/ou SMS.
5. O sistema registra o envio no histórico.

**Fluxos Alternativos**
- **A1 — Falha no envio:** O sistema registra o erro e agenda nova tentativa.
- **A2 — Aluno sem contato cadastrado:** O sistema registra a pendência para ação manual da recepção.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF10, RF04 | RNF01, RNF02 | RN01 |

### DA15 — Enviar Notificação de Vencimento (UC15)

```plantuml
@startuml DA15_NotificacaoVencimento
title DA15 — Enviar Notificação de Vencimento de Mensalidade

start
:Sistema executa rotina automática diária;
:Identifica alunos com vencimento próximo (≤ 5 dias);

if (Há alunos elegíveis?) then (Não)
  stop
else (Sim)
  :Gera mensagem de notificação personalizada;

  if (Aluno possui contato cadastrado?) then (Não)
    :Registra pendência para ação manual da recepção;
    stop
  else (Sim)
    :Envia notificação por e-mail e/ou SMS;
    if (Falha no envio?) then (Sim)
      :Registra erro e agenda nova tentativa;
      stop
    else (Não)
      :Registra envio no histórico;
      stop
    endif
  endif
endif

@enduml
```

---

### UC16 — Enviar Notificação de Confirmação de Agendamento

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Sistema (automático) |
| **Objetivo** | Confirmar ao aluno, via notificação, que seu agendamento de aula foi realizado com sucesso. |

**Pré-condições**
- Agendamento de aula concluído com sucesso (UC07).
- Aluno com e-mail ou telefone válido cadastrado.

**Pós-condições**
- Notificação de confirmação enviada ao aluno.

**Fluxo Principal**
1. O sistema detecta a confirmação de um novo agendamento.
2. O sistema gera mensagem com dados da aula (modalidade, data, hora, instrutor).
3. O sistema envia a notificação ao aluno.
4. O sistema registra o envio.

**Fluxos Alternativos**
- **A1 — Falha no envio:** O sistema registra o erro e tenta reenviar.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF10, RF06 | RNF01, RNF04 | RN02 |

### DA16 — Enviar Notificação de Confirmação de Agendamento (UC16)

```plantuml
@startuml DA16_NotificacaoAgendamento
title DA16 — Enviar Notificação de Confirmação de Agendamento

start
:Sistema detecta confirmação de novo agendamento — UC07;
:Gera mensagem com dados da aula (modalidade, data, hora, instrutor);
:Envia notificação ao aluno;

if (Falha no envio?) then (Sim)
  :Registra erro;
  :Agenda nova tentativa de envio;
  stop
else (Não)
  :Registra envio com sucesso;
  stop
endif

@enduml
```

---

### UC17 — Notificar Liberação de Nova Avaliação Física

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Sistema (automático) |
| **Objetivo** | Informar ao aluno que uma nova avaliação física está disponível para agendamento. |

**Pré-condições**
- Aluno ativo e regular.
- Período mínimo desde a última avaliação atingido (conforme regra da academia).

**Pós-condições**
- Notificação enviada ao aluno.

**Fluxo Principal**
1. O sistema executa rotina de verificação periódica.
2. O sistema identifica alunos elegíveis para nova avaliação.
3. O sistema gera e envia notificação informando a disponibilidade.
4. O sistema registra o envio.

**Fluxos Alternativos**
- **A1 — Aluno inadimplente:** O sistema não envia a notificação até regularização.
- **A2 — Falha no envio:** O sistema registra e agenda reenvio.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF10, RF08 | RNF01 | RN05 |

### DA17 — Notificar Liberação de Avaliação Física (UC17)

```plantuml
@startuml DA17_NotificacaoAvaliacaoFisica
title DA17 — Notificar Liberação de Nova Avaliação Física

start
:Sistema executa rotina de verificação periódica;
:Identifica alunos elegíveis para nova avaliação;

if (Há alunos elegíveis?) then (Não)
  stop
else (Sim)
  :Verifica regularidade de cada aluno — UC05;

  if (Aluno regular e ativo? — RN05) then (Não)
    :Suspende notificação até regularização;
    stop
  else (Sim)
    :Gera e envia notificação de disponibilidade;
    if (Falha no envio?) then (Sim)
      :Registra e agenda reenvio;
      stop
    else (Não)
      :Registra envio;
      stop
    endif
  endif
endif

@enduml
```

---

### UC18 — Consultar Histórico de Avaliações Físicas

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Aluno / Instrutor |
| **Objetivo** | Visualizar o histórico de avaliações físicas realizadas pelo aluno ao longo do tempo. |

**Pré-condições**
- Usuário autenticado.
- Aluno deve ter pelo menos uma avaliação registrada.

**Pós-condições**
- Histórico de avaliações exibido.

**Fluxo Principal**
1. O usuário acessa o módulo de avaliações físicas.
2. O sistema lista todas as avaliações do aluno em ordem cronológica.
3. O usuário seleciona uma avaliação para visualizar os detalhes.
4. O sistema exibe os dados completos e arquivos anexados.

**Fluxos Alternativos**
- **A1 — Nenhuma avaliação registrada:** O sistema informa que não há avaliações no histórico.
- **A2 — Instrutor consulta avaliação de aluno:** O instrutor busca o aluno pelo nome/matrícula e acessa o histórico.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF08 | RNF02, RNF04 | RN06 |

### DA18 — Consultar Histórico de Avaliações Físicas (UC18)

```plantuml
@startuml DA18_ConsultarHistoricoAvaliacoes
title DA18 — Consultar Histórico de Avaliações Físicas

start
:Usuário acessa módulo de avaliações físicas;

if (Usuário é Instrutor?) then (Sim)
  :Busca aluno por nome ou matrícula;
else (Não — Aluno)
  :Sistema identifica o próprio aluno autenticado;
endif

:Sistema lista avaliações em ordem cronológica;

if (Há avaliações registradas?) then (Não)
  :Informa ausência de avaliações no histórico;
  stop
else (Sim)
  :Usuário seleciona uma avaliação;
  :Sistema exibe dados completos e arquivos anexados;
  stop
endif

@enduml
```

---

### UC19 — Editar Dados Cadastrais do Aluno

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Recepcionista |
| **Objetivo** | Atualizar informações cadastrais de um aluno já matriculado (contato, endereço, plano etc.). |

**Pré-condições**
- Recepcionista autenticado no sistema.
- Aluno já cadastrado.

**Pós-condições**
- Dados do aluno atualizados no sistema.

**Fluxo Principal**
1. O recepcionista acessa o módulo de cadastro de alunos.
2. O recepcionista busca o aluno pelo nome ou CPF.
3. O sistema exibe os dados atuais do aluno.
4. O recepcionista edita os campos desejados.
5. O sistema valida os dados alterados.
6. O sistema salva as alterações e confirma a atualização.

**Fluxos Alternativos**
- **A1 — Dados inválidos:** O sistema exibe mensagem de erro indicando os campos com problema.
- **A2 — Aluno não encontrado:** O sistema exibe mensagem e solicita nova busca.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF01, RF02 | RNF02, RNF04 | RN06 |


### DA19 — Editar Dados Cadastrais do Aluno (UC19)

```plantuml
@startuml DA19_EditarDadosCadastrais
title DA19 — Editar Dados Cadastrais do Aluno

start
:Recepcionista acessa módulo de cadastro de alunos;
:Busca aluno por nome ou CPF;

if (Aluno encontrado?) then (Não)
  :Exibe mensagem de erro;
  :Solicita nova busca;
  stop
else (Sim)
  :Sistema exibe dados atuais do aluno;
  :Recepcionista edita os campos desejados;
  :Sistema valida os dados alterados;

  if (Dados válidos?) then (Não)
    :Exibe campos com problema;
    stop
  else (Sim)
    :Salva as alterações;
    :Confirma atualização ao recepcionista;
    stop
  endif
endif

@enduml
```

---

### UC20 — Desativar Matrícula de Aluno

| Campo | Conteúdo |
|---|---|
| **Ator Principal** | Recepcionista / Gerente |
| **Objetivo** | Inativar o cadastro de um aluno que solicitou cancelamento ou que será desligado da academia. |

**Pré-condições**
- Usuário autenticado (Recepcionista ou Gerente).
- Aluno cadastrado e com matrícula ativa.

**Pós-condições**
- Matrícula do aluno inativada.
- Acesso via catraca bloqueado automaticamente.
- Agendamentos futuros cancelados.

**Fluxo Principal**
1. O usuário acessa o módulo de cadastro de alunos.
2. O usuário busca e seleciona o aluno.
3. O usuário seleciona a opção "Desativar Matrícula".
4. O sistema solicita confirmação da ação.
5. O usuário confirma.
6. O sistema inativa a matrícula e bloqueia o RFID.
7. O sistema cancela todos os agendamentos futuros do aluno.
8. O sistema registra a data e motivo do desligamento.

**Fluxos Alternativos**
- **A1 — Aluno com pendências financeiras:** O sistema exibe alerta sobre débitos pendentes antes de confirmar a desativação.
- **A2 — Cancelamento da ação:** O usuário cancela e o sistema mantém a matrícula ativa.

**Requisitos Relacionados**

| RF | RNF | RN |
|---|---|---|
| RF01, RF05, RF06 | RNF02, RNF04 | RN06 |


### DA20 — Desativar Matrícula de Aluno (UC20)

```plantuml
@startuml DA20_DesativarMatricula
title DA20 — Desativar Matrícula de Aluno

start
:Usuário acessa módulo de cadastro de alunos;
:Busca e seleciona o aluno;
:Seleciona opção "Desativar Matrícula";

if (Aluno possui pendências financeiras?) then (Sim)
  :Exibe alerta sobre débitos pendentes;
endif

:Sistema solicita confirmação da ação;

if (Usuário confirma?) then (Não)
  :Mantém matrícula ativa;
  stop
else (Sim)
  :Inativa a matrícula do aluno;
  :Bloqueia cartão RFID;
  :Cancela todos os agendamentos futuros;
  :Registra data e motivo do desligamento;
  stop
endif

@enduml
```