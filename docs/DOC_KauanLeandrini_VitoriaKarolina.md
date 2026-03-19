## DIAGRAMA DE VISÃO GERAL DO SISTEMA:

<img width="4096" height="932" alt="diagrama_UC_geral" src="https://github.com/user-attachments/assets/4db21267-ada1-4313-ab82-27a3b71493c9" />

---

## UC01 - Realizar Login
### Ator Principal
Usuário (qualquer perfil: Aluno, Recepcionista, Instrutor ou Gerente)
### Objetivo
Permitir que o usuário acesse o sistema com seu perfil específico.
### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.
### Pós-condições
- Sessão iniciada com sucesso e menu conforme perfil carregado.
### Fluxo Principal
1. O usuário informa e-mail e senha na tela de login.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial de acordo com o perfil.
### Fluxos Alternativos
- **A1: Credenciais inválidas** - O sistema exibe mensagem de erro e permite nova tentativa (máximo 3 tentativas).
- **A2: Conta bloqueada** - O sistema impede o login e orienta o usuário a recuperar o acesso ou regularizar pagamento.
### Requisitos e Regras
- **RF:** (base para todos os RF)
- **RNF:** RNF02, RNF03
- **RN:** RN06

<img width="609" height="436" alt="diagrama_uc_1" src="https://github.com/user-attachments/assets/acac39c4-2b7d-4341-bb0a-df27062d9aa0" />

---

## UC02 - Cadastrar Aluno
### Ator Principal
Recepcionista
### Objetivo
Registrar um novo aluno no sistema para permitir o uso da academia.
### Pré-condições
Recepcionista autenticado no sistema.
### Pós-condições
Cadastro realizado com sucesso no banco de dados.
### Fluxo Principal
O recepcionista insere os dados pessoais (nome, CPF, contato).
O sistema valida se o CPF é único e se os campos obrigatórios foram preenchidos.
O sistema confirma o salvamento dos dados.
### Fluxos Alternativos
**A1: CPF já cadastrado** - O sistema informa que o aluno já existe e cancela a operação.
### Requisitos e Regras
**RF:** RF01
**RNF:** RNF04
**RN:** RN06

<img width="560" height="411" alt="diagrama_uc_2" src="https://github.com/user-attachments/assets/28122328-c4c6-4f6c-85f6-9c5744d29f62" />

---

## UC03 - Efetuar Matrícula em Plano
### Ator Principal
Recepcionista
### Objetivo
Vincular um aluno a um plano específico de musculação ou aulas.
### Pré-condições
Aluno devidamente cadastrado.
### Pós-condições
Matrícula ativa no sistema vinculada ao perfil do aluno.
### Fluxo Principal
O recepcionista busca o aluno pelo nome ou CPF.
Seleciona o plano desejado (ex: Musculação Mensal).
O sistema gera o registro de matrícula e a primeira parcela financeira.
O recepcionista confirma a finalização da matrícula.
### Requisitos e Regras
**RF:** RF01, RF02
**RN:** RN06

<img width="350" height="430" alt="diagrama_uc_3" src="https://github.com/user-attachments/assets/282d50f3-b7bc-45df-ade9-a0d94f47ffc7" />

---

## UC04 - Validar Acesso via Catraca
### Ator Principal
Sistema de Catraca (API)
### Objetivo
Permitir ou bloquear a entrada física do aluno na unidade.
### Pré-condições
Aluno possuir tag RFID cadastrada e ativa.
### Fluxo Principal
O aluno aproxima a tag da catraca.
O sistema consulta a regularidade financeira do aluno em tempo real.
O sistema envia comando de liberação para a catraca girar.
### Fluxos Alternativos
**A1: Inadimplência** - Se o pagamento estiver vencido há mais de 5 dias, o sistema bloqueia o acesso e exibe mensagem de erro na catraca.
### Requisitos e Regras
**RF:** RF05, RF04
**RNF:** RNF03, RNF06
**RN:** RN01

<img width="434" height="430" alt="diagrama_uc_4" src="https://github.com/user-attachments/assets/dcbec8cb-6c11-4f21-92a4-24bcfb6878df" />

---

## UC05 - Registrar Pagamento
### Ator Principal
Recepcionista
### Objetivo
Registrar a entrada de valores e dar baixa em parcelas do aluno.
### Pós-condições
Situação financeira do aluno atualizada instantaneamente para "Regular".
### Fluxo Principal
O recepcionista acessa o módulo financeiro do aluno.
Seleciona a parcela que está em aberto.
Informa o método de pagamento (Dinheiro, Cartão ou PIX).
O sistema confirma o recebimento do valor integral.
### Requisitos e Regras
**RF:** RF03
**RN:** RN04, RN07

<img width="522" height="485" alt="diagrama_uc_5" src="https://github.com/user-attachments/assets/92a7cc04-3f4f-4ff1-b5cc-112beb6197f7" />

---

## UC06 - Agendar Aula Coletiva
### Ator Principal
Aluno
### Objetivo
Garantir uma vaga em uma modalidade específica com horário marcado.
### Fluxo Principal
O aluno consulta a grade de aulas disponíveis no aplicativo/sistema.
Seleciona a aula desejada e confirma a reserva.
O sistema verifica se o limite de vagas ainda não foi atingido.
O agendamento é confirmado com sucesso.
### Fluxos Alternativos
**A1: Limite de vagas atingido** - O sistema impede o agendamento e avisa que a turma está lotada.
### Requisitos e Regras
**RF:** RF06
**RN:** RN02

<img width="316" height="485" alt="diagrama_uc_6" src="https://github.com/user-attachments/assets/09963987-cc4b-40ef-beb7-ffd9028a964f" />

---

## UC07 - Cancelar Agendamento de Aula
### Ator Principal
Aluno
### Objetivo
Remover a reserva de uma aula para liberar a vaga para outros.
### Fluxo Principal
O aluno visualiza sua lista de agendamentos ativos.
Solicita o cancelamento da aula selecionada.
O sistema valida se o tempo atual é superior a 1 hora do início da aula.
A vaga é liberada e o agendamento removido.
### Fluxos Alternativos
**A1: Fora do prazo** - O sistema impede o cancelamento por estar a menos de 1 hora do início.
### Requisitos e Regras
**RF:** RF06
**RN:** RN03

<img width="406" height="374" alt="diagrama_uc_7" src="https://github.com/user-attachments/assets/dc456b78-6923-49c3-99cf-204852b4baec" />

---

## UC08 - Registrar Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Cadastrar medidas corporais e índices de saúde do aluno.
### Pré-condições
Aluno estar com a situação financeira regular.
### Fluxo Principal
O instrutor seleciona o aluno no sistema.
Insere os dados coletados (peso, IMC, percentual de gordura).
O sistema salva a avaliação e notifica o aluno automaticamente.
### Requisitos e Regras
**RF:** RF08, RF10
**RN:** RN05, RN06

<img width="462" height="374" alt="diagrama_uc_8" src="https://github.com/user-attachments/assets/aed16fb2-6797-4b37-bea8-f0a4aa9cde9b" />

---

## UC09 - Registrar Presença (Lista)
### Ator Principal
Instrutor
### Objetivo
Confirmar a participação real dos alunos que agendaram a aula.
### Fluxo Principal
O instrutor acessa a lista de agendados para a turma atual.
Marca os alunos que compareceram à sala.
O sistema armazena o histórico de presença para relatórios.
### Requisitos e Regras
**RF:** RF07
**RN:** RN06

<img width="253" height="340" alt="diagrama_uc_9" src="https://github.com/user-attachments/assets/11adb087-85bc-4ba0-b684-f0d81fe5a56f" />

---

## UC010 - Emitir Relatório de Inadimplência
### Ator Principal
Gerente
### Objetivo
Listar todos os alunos que possuem mensalidades em atraso.
### Fluxo Principal
O gerente acessa o módulo de relatórios gerenciais.
Seleciona o filtro específico de inadimplência.
O sistema gera a listagem de nomes e valores pendentes.
### Requisitos e Regras
**RF:** RF09
**RN:** RN06

<img width="349" height="340" alt="diagrama_uc_10" src="https://github.com/user-attachments/assets/18b854ea-4b12-489f-89a3-e8e8822dd195" />

---

## UC11 - Gerenciar Planos
### Ator Principal
Gerente
### Objetivo
Configurar novos valores, nomes e durações dos planos oferecidos.
### Fluxo Principal
O gerente acessa as configurações de sistema para planos.
Define nome do plano, preço e tempo de contrato.
O sistema atualiza as opções disponíveis para a recepção realizar vendas.
### Requisitos e Regras
**RF:** RF02
**RN:** RN06

<img width="381" height="349" alt="diagrama_uc_11" src="https://github.com/user-attachments/assets/9e167b5b-9eda-4b86-88e0-b7075b10f853" />

---

## UC12 - Emitir Relatório de Histórico de Acessos
### Ator Principal
Gerente
### Objetivo
Visualizar entradas/saídas de alunos.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Relatório exibido.
### Fluxo Principal
1. Seleciona "Histórico de Acessos".
2. Filtra por aluno/período.
3. Mostra datas, horários e status.
### Fluxos Alternativos
- **A1: Período sem registros** - Exibe "Nenhum acesso registrado".
### Requisitos e Regras
- **RF:** RF09
- **RNF:** RNF03
- **RN:** RN01

<img width="334" height="285" alt="diagrama_uc_12" src="https://github.com/user-attachments/assets/26fb8bae-f2ad-4574-8970-e30cd354a8e0" />

---

## UC13 - Emitir Relatório de Ocupação das Aulas
### Ator Principal
Gerente
### Objetivo
Analisar vagas ocupadas por aula.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Relatório gerado com gráficos/tabelas.
### Fluxo Principal
1. Seleciona "Ocupação das Aulas".
2. Filtra por período/modalidade.
3. Exibe % de ocupação e horários pico.
### Fluxos Alternativos
- **A1: Nenhuma aula no período** - Exibe "Nenhuma aula encontrada".
### Requisitos e Regras
- **RF:** RF09
- **RNF:** RNF04
- **RN:** RN02

<img width="327" height="340" alt="diagrama_uc_13" src="https://github.com/user-attachments/assets/24d2e8bb-cf67-4636-ab46-fb2a71f5253b" />

---

## UC14 - Enviar Notificação de Vencimento
### Ator Principal
Sistema (automático)
### Objetivo
Notificar aluno sobre mensalidade próxima do vencimento.
### Pré-condições
- Aluno com vencimento próximo.
### Pós-condições
- Notificação enviada (e-mail/app).
### Fluxo Principal
1. Sistema verifica diariamente vencimentos próximos.
2. Envia lembrete automático.
### Fluxos Alternativos
- **A1: Vencido** - Envia alerta de inadimplência.
### Requisitos e Regras
- **RF:** RF10
- **RNF:** RNF01
- **RN:** RN07

<img width="437" height="307" alt="diagrama_uc_14" src="https://github.com/user-attachments/assets/949e9175-cfe3-43a8-a085-5f1976ddbe90" />

---

## UC15 - Consultar Plano e Status do Aluno
### Ator Principal
Aluno
### Objetivo
Visualizar plano contratado e regularidade.
### Pré-condições
- Aluno autenticado.
### Pós-condições
- Informações exibidas.
### Fluxo Principal
1. Aluno acessa "Meu Perfil/Plano".
2. Sistema mostra plano, vencimento e status.
### Fluxos Alternativos
- **A1: Aluno inadimplente** - Exibe status “Bloqueado” e botão para regularizar pagamento.
### Requisitos e Regras
- **RF:** RF01, RF04
- **RNF:** RNF04
- **RN:** RN07

<img width="340" height="230" alt="diagrama_uc_15" src="https://github.com/user-attachments/assets/5530eb52-fba2-440d-8d53-98f092560f63" />

---

## UC16 - Visualizar e Reservar Aulas Disponíveis
### Ator Principal
Aluno
### Objetivo
Ver horários disponíveis e realizar reserva.
### Pré-condições
- Aluno regular e autenticado.
### Pós-condições
- Reserva realizada ou mensagem de lotação.
### Fluxo Principal
1. Aluno acessa “Aulas Disponíveis”.
2. Visualiza grade horária.
3. Seleciona aula e confirma reserva.
### Fluxos Alternativos
- **A1: Vagas esgotadas** - Sistema bloqueia e sugere horários alternativos.
### Requisitos e Regras
- **RF:** RF06
- **RNF:** RNF04
- **RN:** RN02

<img width="309" height="340" alt="diagrama_uc_16" src="https://github.com/user-attachments/assets/7efb0280-404f-4071-98bf-bdce8401d3c8" />

---

## UC17 - Recuperar Senha Esquecida
### Ator Principal
Usuário
### Objetivo
Recuperar acesso via e-mail.
### Pré-condições
- E-mail cadastrado.
### Pós-condições
- Link de reset enviado.
### Fluxo Principal
1. Usuário clica “Esqueci minha senha”.
2. Informa e-mail.
3. Sistema envia link temporário.
### Fluxos Alternativos
- **A1: E-mail não encontrado** - Exibe mensagem “E-mail não cadastrado”.
### Requisitos e Regras
- **RF:** (base para login)
- **RNF:** RNF02
- **RN:** RN06

<img width="347" height="319" alt="diagrama_uc_17" src="https://github.com/user-attachments/assets/8584ca4d-5a72-4558-a33c-f69a05a5de66" />

---

## UC18 - Realizar Check-in Manual (sem catraca)
### Ator Principal
Recepcionista ou Aluno (via app)
### Objetivo
Registrar presença manualmente.
### Pré-condições
- Aluno regular.
### Pós-condições
- Acesso registrado no histórico.
### Fluxo Principal
1. Busca aluno.
2. Confirma regularidade.
3. Registra entrada manual.
### Fluxos Alternativos
- **A1: Aluno inadimplente** - Sistema bloqueia e orienta regularização.
### Requisitos e Regras
- **RF:** RF05
- **RNF:** RNF03
- **RN:** RN01

<img width="395" height="319" alt="diagrama_uc_18" src="https://github.com/user-attachments/assets/0ea931c0-2e72-4b64-8589-1c6fc2b6807a" />

---

## UC19 - Anexar Arquivo na Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Anexar fotos/medidas extras na avaliação.
### Pré-condições
- Avaliação em andamento.
### Pós-condições
- Arquivo salvo e associado ao registro.
### Fluxo Principal
1. Durante o registro de avaliação, seleciona “Anexar arquivo”.
2. Faz upload.
3. Sistema associa ao aluno.
### Fluxos Alternativos
- **A1: Arquivo maior que limite** - Exibe erro e orienta redimensionar.
### Requisitos e Regras
- **RF:** RF08
- **RNF:** RNF02
- **RN:** RN05

<img width="318" height="340" alt="diagrama_uc_19" src="https://github.com/user-attachments/assets/a2a6dd58-a5d4-453f-8e29-5dedd537a1d5" />

---

## UC20 - Visualizar Histórico de Avaliações Físicas
### Ator Principal
Instrutor ou Aluno
### Objetivo
Consultar evolução das avaliações físicas.
### Pré-condições
- Usuário autenticado com permissão.
### Pós-condições
- Histórico exibido com gráficos.
### Fluxo Principal
1. Busca aluno.
2. Acessa “Histórico de Avaliações”.
3. Sistema mostra comparativos e gráficos.
### Fluxos Alternativos
- **A1: Nenhum registro** - Exibe “Nenhuma avaliação encontrada”.
### Requisitos e Regras
- **RF:** RF08, RF09
- **RNF:** RNF04
- **RN:** RN06

<img width="332" height="285" alt="diagrama_uc_20" src="https://github.com/user-attachments/assets/effc8eb5-fec9-4a5a-ae70-62ad318c7467" />

---

## UC21 - Gerar Boleto ou Link de Pagamento Online
### Ator Principal
Recepcionista
### Objetivo
Gerar boleto bancário ou link de pagamento PIX para o aluno realizar pagamento online.
### Pré-condições
- Recepcionista autenticado e aluno selecionado com mensalidade pendente.
### Pós-condições
- Boleto ou link gerado, enviado ao aluno e registro criado no sistema.
### Fluxo Principal
1. Recepcionista busca o aluno pelo nome ou matrícula.
2. Acessa a opção “Gerar Pagamento Online”.
3. Sistema calcula valor total devido.
4. Recepcionista escolhe boleto ou PIX e confirma.
5. Sistema gera o documento/link e envia automaticamente por e-mail/WhatsApp.
### Fluxos Alternativos
- **A1: Aluno sem pendência** - Sistema exibe mensagem “Aluno está com pagamento em dia” e não gera boleto.
- **A2: Erro na integração com gateway de pagamento** - Sistema exibe erro e permite tentar novamente em 30 segundos.
### Requisitos e Regras
- **RF:** RF03
- **RNF:** RNF03, RNF04
- **RN:** RN04, RN07

<img width="373" height="396" alt="diagrama_uc_21" src="https://github.com/user-attachments/assets/80c3b474-2a7a-4363-afb9-f919048cd1f9" />

---
