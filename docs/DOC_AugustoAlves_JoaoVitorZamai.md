# Casos de Uso – Sistema FitPass Gym Management

<img width="517" height="2054" alt="image" src="https://github.com/user-attachments/assets/0f7e6d92-33ec-4a89-af18-6bbca615b6b5" />

---

## UC01 — Realizar Login

### Ator Principal
Usuário

### Objetivo
Permitir que um usuário autenticado acesse o sistema de gestão da academia.

### Pré-condições
- O usuário deve possuir cadastro ativo no sistema.
- O usuário deve possuir credenciais válidas.

### Pós-condições
- Sessão do usuário iniciada.
- Usuário redirecionado para o painel inicial do sistema.

### Fluxo Principal
1. O usuário acessa a tela de login.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais.
4. O sistema autentica o usuário.
5. O sistema redireciona o usuário para a tela inicial.

### Fluxos Alternativos
- *A1 — Senha incorreta:*  
  O sistema exibe mensagem informando que as credenciais são inválidas.

- *A2 — Conta bloqueada:*  
  O sistema impede o login e orienta o usuário a recuperar o acesso.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF01 — Segurança de autenticação
- RNF02 — Disponibilidade do sistema

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="952" height="477" alt="image" src="https://github.com/user-attachments/assets/7ed4ac7b-58ab-479e-9ef9-c94821d873fd" />

---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Permitir o cadastro de novos alunos no sistema da academia.

### Pré-condições
- O recepcionista deve estar autenticado no sistema.

### Pós-condições
- Aluno registrado no banco de dados.
- Aluno apto a contratar planos.

### Fluxo Principal
1. O recepcionista acessa o módulo de cadastro de alunos.
2. O recepcionista informa os dados pessoais do aluno.
3. O recepcionista informa dados de contato e endereço.
4. O recepcionista seleciona o plano contratado.
5. O sistema valida as informações.
6. O sistema registra o novo aluno.

### Fluxos Alternativos
- *A1 — Dados obrigatórios ausentes:*  
  O sistema solicita o preenchimento dos campos obrigatórios.

- *A2 — Aluno já cadastrado:*  
  O sistema informa que já existe cadastro com os mesmos dados.

### RF Relacionados
- RF01 — Cadastro de Alunos
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="993" height="582" alt="image" src="https://github.com/user-attachments/assets/b226960b-c86d-4492-99de-21642c8a8523" />


---

## UC03 — Atualizar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Permitir atualizar dados cadastrais de alunos.

### Pré-condições
- O aluno deve existir no sistema.

### Pós-condições
- Dados do aluno atualizados.

### Fluxo Principal
1. O recepcionista busca o aluno no sistema.
2. O sistema exibe os dados cadastrados.
3. O recepcionista altera as informações necessárias.
4. O sistema valida os dados.
5. O sistema salva as alterações.

### Fluxos Alternativos
- *A1 — Aluno não encontrado:*  
  O sistema informa que o aluno não foi localizado.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="842" height="476" alt="image" src="https://github.com/user-attachments/assets/be559afa-65ef-454f-a3c4-dd6efc8bb6ab" />


---

## UC04 — Criar Plano

### Ator Principal
Gerente

### Objetivo
Permitir cadastrar novos planos de academia.

### Pré-condições
- O gerente deve estar autenticado.

### Pós-condições
- Novo plano disponível para contratação.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O gerente seleciona a opção criar plano.
3. O gerente informa nome, duração e valor do plano.
4. O sistema valida os dados.
5. O sistema registra o novo plano.

### Fluxos Alternativos
- *A1 — Dados inválidos:*  
  O sistema solicita correção das informações.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="692" height="462" alt="image" src="https://github.com/user-attachments/assets/12f5c963-a6e7-417f-bf0f-68a985cf2ec8" />

---

## UC05 — Editar Plano

### Ator Principal
Gerente

### Objetivo
Permitir modificar informações de um plano existente.

### Pré-condições
- Plano deve estar cadastrado.

### Pós-condições
- Plano atualizado no sistema.

### Fluxo Principal
1. O gerente acessa a lista de planos.
2. O gerente seleciona um plano.
3. O gerente altera as informações.
4. O sistema valida as alterações.
5. O sistema salva o plano atualizado.

### Fluxos Alternativos
- *A1 — Plano inexistente:*  
  O sistema informa erro de localização.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="675" height="476" alt="image" src="https://github.com/user-attachments/assets/0594f50e-57cd-46f5-8c40-c3c94beb58ee" />

---

## UC06 — Registrar Pagamento

### Ator Principal
Recepcionista

### Objetivo
Registrar pagamento da mensalidade de um aluno.

### Pré-condições
- Aluno deve estar cadastrado.

### Pós-condições
- Pagamento registrado.
- Situação do aluno atualizada.

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O recepcionista seleciona registrar pagamento.
3. O recepcionista informa forma de pagamento.
4. O sistema registra a transação.
5. O sistema atualiza a regularidade do aluno.

### Fluxos Alternativos
- *A1 — Valor incorreto:*  
  O sistema rejeita o pagamento.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF04 — Segurança financeira

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade
<img width="815" height="462" alt="image" src="https://github.com/user-attachments/assets/50a9056e-1663-4ce1-9713-a3dd2b9bfacc" />

---

## UC07 — Verificar Regularidade do Aluno

### Ator Principal
Sistema

### Objetivo
Verificar automaticamente se o aluno está com mensalidade em dia.

### Pré-condições
- Aluno cadastrado.

### Pós-condições
- Status de regularidade atualizado.

### Fluxo Principal
1. O sistema verifica a data do último pagamento.
2. O sistema compara com a data atual.
3. O sistema define o status como regular ou inadimplente.

### Fluxos Alternativos
- *A1 — Pagamento recente:*  
  O sistema mantém o status regular.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF05 — Processamento automático

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
<img width="439" height="315" alt="image" src="https://github.com/user-attachments/assets/85a62c56-03bb-4cfd-b6e0-bf2c68757f93" />

---

## UC08 — Validar Entrada na Catraca

### Ator Principal
Aluno

### Objetivo
Permitir acesso do aluno à academia por meio de RFID.

### Pré-condições
- Aluno cadastrado.
- Aluno com cartão RFID.

### Pós-condições
- Entrada liberada ou bloqueada.

### Fluxo Principal
1. O aluno aproxima o cartão RFID da catraca.
2. O sistema identifica o aluno.
3. O sistema verifica regularidade.
4. O sistema libera a catraca.

### Fluxos Alternativos
- *A1 — Aluno inadimplente:*  
  A entrada é bloqueada.

### RF Relacionados
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF06 — Tempo de resposta rápido

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
<img width="662" height="405" alt="image" src="https://github.com/user-attachments/assets/a9dfec04-73f4-4926-ab03-44b79306ed1b" />

---

## UC09 — Visualizar Aulas Disponíveis

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize os horários das aulas.

### Pré-condições
- Aluno autenticado.

### Pós-condições
- Lista de aulas exibida.

### Fluxo Principal
1. O aluno acessa o módulo de aulas.
2. O sistema exibe as aulas disponíveis.
3. O aluno visualiza horários e vagas.

### Fluxos Alternativos
- *A1 — Nenhuma aula disponível:*  
  O sistema exibe mensagem informativa.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF02 — Disponibilidade

### RN Relacionadas
- RN02 — Limite de vagas
<img width="715" height="363" alt="image" src="https://github.com/user-attachments/assets/794b1826-69a4-4fd5-8941-7f82dd1cf779" />

---

## UC10 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Permitir reservar vaga em uma aula.

### Pré-condições
- Aluno autenticado.
- Aula disponível.

### Pós-condições
- Reserva registrada.

### Fluxo Principal
1. O aluno seleciona uma aula.
2. O aluno confirma o agendamento.
3. O sistema verifica disponibilidade.
4. O sistema registra a reserva.

### Fluxos Alternativos
- *A1 — Aula lotada:*  
  O sistema impede o agendamento.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN02 — Limite de vagas
<img width="671" height="405" alt="image" src="https://github.com/user-attachments/assets/a6bd1650-3141-47e9-886f-58eeadaac95a" />

---

## UC11 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Permitir cancelar uma reserva de aula.

### Pré-condições
- Reserva existente.

### Pós-condições
- Vaga liberada.

### Fluxo Principal
1. O aluno acessa suas reservas.
2. O aluno seleciona cancelar reserva.
3. O sistema verifica horário.
4. O sistema cancela a reserva.

### Fluxos Alternativos
- *A1 — Cancelamento fora do prazo:*  
  O sistema impede o cancelamento.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN03 — Cancelamento de agendamento
<img width="776" height="405" alt="image" src="https://github.com/user-attachments/assets/dfdc48cf-a475-4b28-a1b2-f34d6096f406" />

---

## UC12 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Registrar presença dos alunos.

### Pré-condições
- Aula iniciada.

### Pós-condições
- Presença registrada.

### Fluxo Principal
1. O instrutor abre a lista da aula.
2. O instrutor marca presença dos alunos.
3. O sistema salva os registros.

### Fluxos Alternativos
- *A1 — Aluno não compareceu:*  
  Presença marcada como ausência.

### RF Relacionados
- RF07 — Lista de Presença

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="640" height="302" alt="image" src="https://github.com/user-attachments/assets/9d3223a4-0107-4914-9931-c5977aaa24bf" />

---

## UC13 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar dados de avaliação física.

### Pré-condições
- Aluno ativo.

### Pós-condições
- Avaliação salva no histórico.

### Fluxo Principal
1. O instrutor seleciona o aluno.
2. O instrutor insere dados de avaliação.
3. O sistema valida os dados.
4. O sistema salva a avaliação.

### Fluxos Alternativos
- *A1 — Aluno irregular:*  
  Avaliação não permitida.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF03 — Integridade de dados

### RN Relacionadas
- RN05 — Avaliação física
<img width="735" height="419" alt="image" src="https://github.com/user-attachments/assets/f939e52f-7891-439f-8e4b-cbcfe6deda58" />

---

## UC14 — Anexar Arquivo de Avaliação

### Ator Principal
Instrutor

### Objetivo
Adicionar arquivos relacionados à avaliação física.

### Pré-condições
- Avaliação criada.

### Pós-condições
- Arquivo armazenado.

### Fluxo Principal
1. O instrutor acessa a avaliação.
2. O instrutor seleciona anexar arquivo.
3. O sistema realiza upload.
4. O sistema salva o arquivo.

### Fluxos Alternativos
- *A1 — Arquivo inválido:*  
  O sistema rejeita o upload.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF07 — Armazenamento de arquivos

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="639" height="462" alt="image" src="https://github.com/user-attachments/assets/e9e8256c-a4ab-4867-9f02-ce0803e6bcbe" />

---

## UC15 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Gerar relatório de alunos inadimplentes.

### Pré-condições
- Usuário gerente autenticado.

### Pós-condições
- Relatório gerado.

### Fluxo Principal
1. O gerente acessa relatórios.
2. O gerente seleciona inadimplência.
3. O sistema consulta dados.
4. O sistema gera relatório.

### Fluxos Alternativos
- *A1 — Sem inadimplentes:*  
  O sistema informa que não há registros.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF08 — Desempenho de consultas

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
<img width="579" height="405" alt="image" src="https://github.com/user-attachments/assets/ab4d884b-62f0-46a5-82df-60daaed895e2" />

---

## UC16 — Emitir Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Listar alunos com matrícula ativa.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório exibido.

### Fluxo Principal
1. O gerente seleciona relatório de alunos ativos.
2. O sistema consulta os registros.
3. O sistema gera o relatório.

### Fluxos Alternativos
- *A1 — Nenhum aluno ativo:*  
  O sistema exibe aviso.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF08 — Desempenho

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="638" height="349" alt="image" src="https://github.com/user-attachments/assets/b6841116-4db8-43f6-865d-75cc60b55cdb" />

---

## UC17 — Emitir Relatório de Acessos

### Ator Principal
Gerente

### Objetivo
Visualizar histórico de entradas na academia.

### Pré-condições
- Registros de acesso disponíveis.

### Pós-condições
- Relatório exibido.

### Fluxo Principal
1. O gerente acessa relatórios.
2. O gerente seleciona histórico de acessos.
3. O sistema consulta registros RFID.
4. O sistema apresenta relatório.

### Fluxos Alternativos
- *A1 — Sem registros:*  
  O sistema informa ausência de dados.

### RF Relacionados
- RF09 — Relatórios Gerenciais
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF08 — Desempenho

### RN Relacionadas
- RN06 — Acesso restrito por perfil
<img width="608" height="405" alt="image" src="https://github.com/user-attachments/assets/c40b4a92-1e53-4176-b14a-039e221b3629" />

---

## UC18 — Emitir Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Analisar ocupação das aulas.

### Pré-condições
- Aulas registradas no sistema.

### Pós-condições
- Relatório gerado.

### Fluxo Principal
1. O gerente seleciona relatório de ocupação.
2. O sistema calcula taxa de ocupação.
3. O sistema apresenta relatório.

### Fluxos Alternativos
- *A1 — Nenhuma aula cadastrada:*  
  O sistema informa ausência de dados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF08 — Desempenho

### RN Relacionadas
- RN02 — Limite de vagas
<img width="632" height="349" alt="image" src="https://github.com/user-attachments/assets/57f592eb-4e84-47cf-a030-8ca686019fe6" />

---

## UC19 — Enviar Notificação de Vencimento

### Ator Principal
Sistema

### Objetivo
Notificar aluno sobre vencimento da mensalidade.

### Pré-condições
- Aluno cadastrado com pagamento próximo ao vencimento.

### Pós-condições
- Notificação enviada.

### Fluxo Principal
1. O sistema identifica mensalidades próximas do vencimento.
2. O sistema gera mensagem de aviso.
3. O sistema envia notificação ao aluno.

### Fluxos Alternativos
- *A1 — Falha no envio:*  
  O sistema registra tentativa e agenda novo envio.

### RF Relacionados
- RF10 — Notificações

### RNF Relacionados
- RNF09 — Entrega de mensagens

### RN Relacionadas
- RN07 — Atualização automática da regularidade
<img width="472" height="371" alt="image" src="https://github.com/user-attachments/assets/da2ed7d1-ccd1-487d-93e9-53dbf6346fe0" />

---

## UC20 — Enviar Notificação de Agendamento

### Ator Principal
Sistema

### Objetivo
Confirmar agendamento de aula para o aluno.

### Pré-condições
- Agendamento registrado.

### Pós-condições
- Notificação enviada ao aluno.

### Fluxo Principal
1. O sistema registra o agendamento.
2. O sistema gera mensagem de confirmação.
3. O sistema envia a notificação.

### Fluxos Alternativos
- *A1 — Falha de envio:*  
  O sistema registra erro e tenta novamente.

### RF Relacionados
- RF10 — Notificações
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF09 — Entrega de mensagens

### RN Relacionadas
- RN02 — Limite de vagas
<img width="437" height="371" alt="image" src="https://github.com/user-attachments/assets/3df49541-e888-4279-9548-e4879fe11c5c" />

