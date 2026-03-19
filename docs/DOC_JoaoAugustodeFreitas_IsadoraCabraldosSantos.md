# Documento de Casos de Uso com Diagramas de Atividade
## Sistema FitPass Gym Management

**Alunos:** João Augusto de Freitas e Isadora Cabral dos Santos  

---

## Índice
1. [Diagrama Geral de Casos de Uso](#diagrama-geral)
2. [Casos de Uso e Diagramas de Atividade](#casos-de-uso)
   - UC01: Realizar Login
   - UC02: Cadastrar Aluno
   - UC03: Editar Dados do Aluno
   - UC04: Gerenciar Planos
   - UC05: Registrar Pagamento
   - UC06: Verificar Regularidade do Aluno
   - UC07: Controlar Acesso por Catraca
   - UC08: Consultar Horários de Aulas
   - UC09: Agendar Aula
   - UC10: Cancelar Agendamento de Aula
   - UC11: Registrar Presença em Aula
   - UC12: Registrar Avaliação Física
   - UC13: Visualizar Histórico de Avaliações Físicas
   - UC14: Emitir Relatório de Inadimplência
   - UC15: Emitir Relatório de Alunos Ativos
   - UC16: Emitir Relatório de Histórico de Acessos
   - UC17: Emitir Relatório de Ocupação das Aulas
   - UC18: Enviar Notificação de Vencimento de Mensalidade
   - UC19: Gerar Boleto / Token de Pagamento Online
   - UC20: Gerenciar Usuários e Perfis de Acesso

---

## Diagrama Geral de Casos de Uso {#diagrama-geral}

![DUC_GERAL](uml/DUC_GERAL.png)

---

## Casos de Uso e Diagramas de Atividade {#casos-de-uso}

---

# UC01 — Realizar Login

## Especificação

### Ator Principal
Aluno, Recepcionista, Instrutor, Gerente

### Objetivo
Permitir que o usuário acesse o sistema com suas credenciais.

### Pré-condições
- O usuário deve possuir cadastro ativo no sistema.
- O sistema deve estar disponível.

### Pós-condições
- Sessão iniciada com sucesso e usuário redirecionado para a tela inicial de acordo com seu perfil.

### Fluxo Principal
1. O usuário acessa a tela de login.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais.
4. O sistema identifica o perfil do usuário (Aluno, Recepcionista, Instrutor ou Gerente).
5. O sistema inicia a sessão e redireciona para a tela inicial do perfil correspondente.

### Fluxos Alternativos
- **A1 — Credenciais inválidas:**
  O sistema exibe mensagem de erro informando que e-mail ou senha estão incorretos. O usuário pode tentar novamente.

- **A2 — Conta bloqueada por inadimplência:**
  O sistema exibe mensagem informando que o acesso está bloqueado e orienta o usuário a regularizar a situação na recepção.

- **A3 — Esqueci minha senha:**
  O usuário solicita redefinição. O sistema envia e-mail de recuperação e aguarda ação do usuário.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC01_Atividade](uml/UC01_Atividade.png)

---

# UC02 — Cadastrar Aluno

## Especificação

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema com todos os dados necessários para matrícula.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- O aluno não deve possuir cadastro ativo com o mesmo CPF ou e-mail.

### Pós-condições
- Aluno cadastrado com situação ativa no sistema.
- Plano contratado vinculado ao cadastro do aluno.
- Cartão RFID associado ao aluno.

### Fluxo Principal
1. A recepcionista acessa a tela de cadastro de aluno.
2. A recepcionista preenche os dados pessoais: nome, CPF, data de nascimento, telefone e e-mail.
3. A recepcionista preenche o endereço do aluno.
4. A recepcionista seleciona o plano contratado.
5. O sistema valida os dados inseridos.
6. O sistema associa um cartão RFID ao aluno.
7. O sistema salva o cadastro e exibe confirmação.

### Fluxos Alternativos
- **A1 — CPF ou e-mail já cadastrado:**
  O sistema exibe mensagem de duplicidade e impede o cadastro.

- **A2 — Dados obrigatórios não preenchidos:**
  O sistema destaca os campos faltantes e solicita preenchimento.

- **A3 — Nenhum plano ativo disponível:**
  O sistema alerta a recepcionista e sugere criar um plano antes de prosseguir.

### RF Relacionados
- RF01 — Cadastro de Alunos
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC02_Atividade](uml/UC02_Atividade.png)

---

# UC03 — Editar Dados do Aluno

## Especificação

### Ator Principal
Recepcionista

### Objetivo
Atualizar informações cadastrais de um aluno existente.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- O aluno deve estar cadastrado no sistema.

### Pós-condições
- Dados do aluno atualizados e salvos no sistema.

### Fluxo Principal
1. A recepcionista busca o aluno pelo nome, CPF ou código.
2. O sistema exibe os dados cadastrais do aluno.
3. A recepcionista edita os campos desejados.
4. O sistema valida as alterações.
5. O sistema salva e exibe confirmação da atualização.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema exibe mensagem informando que o aluno não foi localizado.

- **A2 — Dados inválidos:**
  O sistema destaca os campos inválidos e solicita correção.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC03_Atividade](uml/UC03_Atividade.png)

---

# UC04 — Gerenciar Planos

## Especificação

### Ator Principal
Gerente

### Objetivo
Criar, editar, ativar e desativar planos disponíveis na academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Plano criado, atualizado ou com status alterado conforme ação realizada.

### Fluxo Principal
1. O gerente acessa o módulo de gerenciamento de planos.
2. O gerente seleciona a ação desejada: criar, editar, ativar ou desativar.
3. Para criar/editar: o gerente preenche nome, descrição, valor e modalidade do plano.
4. O sistema valida as informações inseridas.
5. O sistema salva as alterações e exibe confirmação.

### Fluxos Alternativos
- **A1 — Desativar plano com alunos vinculados:**
  O sistema alerta que o plano possui alunos e solicita confirmação antes de desativar.

- **A2 — Plano com nome já existente:**
  O sistema exibe mensagem de duplicidade e impede a criação.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF04 — Usabilidade
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC04_Atividade](uml/UC04_Atividade.png)

---

# UC05 — Registrar Pagamento

## Especificação

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade de um aluno.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- O aluno deve estar cadastrado no sistema.
- O valor da mensalidade deve ser integral.

### Pós-condições
- Pagamento registrado no sistema.
- Situação do aluno atualizada para regular.
- Recibo disponível para impressão ou envio digital.

### Fluxo Principal
1. A recepcionista busca o aluno pelo nome, CPF ou código.
2. O sistema exibe os dados do aluno e o valor da mensalidade em aberto.
3. A recepcionista seleciona a forma de pagamento: dinheiro, cartão ou PIX.
4. O sistema registra o pagamento.
5. O sistema atualiza automaticamente a situação do aluno para regular.
6. O sistema gera e exibe o recibo de pagamento.

### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:**
  O sistema recusa o pagamento e exibe mensagem informando que somente o valor integral é aceito.

- **A2 — Problema na integração de pagamento:**
  O sistema exibe mensagem de erro e sugere tentar novamente ou registrar manualmente.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade

## Diagrama de Fluxo da Atividade

![UC05_Atividade](uml/UC05_Atividade.png)

---

# UC06 — Verificar Regularidade do Aluno

## Especificação

### Ator Principal
Sistema, Recepcionista

### Objetivo
Verificar automaticamente se o aluno possui mensalidade em dia para permitir acesso ou agendamentos.

### Pré-condições
- O aluno deve estar cadastrado no sistema.

### Pós-condições
- Situação de regularidade do aluno confirmada ou negada.

### Fluxo Principal
1. O sistema identifica o aluno (por RFID, CPF ou código).
2. O sistema consulta a data de vencimento da mensalidade do aluno.
3. O sistema verifica se o pagamento está em dia (tolerância de até 5 dias).
4. O sistema retorna o status: regular ou inadimplente.

### Fluxos Alternativos
- **A1 — Aluno inadimplente há mais de 5 dias:**
  O sistema bloqueia o acesso e notifica o aluno sobre a pendência financeira.

- **A2 — Aluno sem plano ativo:**
  O sistema bloqueia o acesso e orienta o aluno a procurar a recepção.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

## Diagrama de Fluxo da Atividade

![UC06_Atividade](uml/UC06_Atividade.png)

---

# UC07 — Controlar Acesso por Catraca

## Especificação

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Validar e liberar ou bloquear o acesso físico do aluno à academia via cartão RFID.

### Pré-condições
- O aluno deve possuir cartão RFID ativo e associado ao seu cadastro.
- O sistema de catraca deve estar conectado ao sistema via API REST.

### Pós-condições
- Acesso liberado e entrada registrada, ou acesso negado com motivo registrado.

### Fluxo Principal
1. O aluno aproxima o cartão RFID da catraca.
2. O sistema de catraca envia o código RFID para o sistema via API REST.
3. O sistema consulta o cadastro do aluno pelo código RFID.
4. O sistema verifica a regularidade do aluno (UC06).
5. O sistema retorna liberação da catraca via API.
6. A catraca registra a entrada e libera a passagem.

### Fluxos Alternativos
- **A1 — Aluno inadimplente:**
  O sistema retorna bloqueio. A catraca não libera a passagem e exibe mensagem de acesso negado.

- **A2 — RFID não cadastrado:**
  O sistema retorna erro. A catraca bloqueia e registra tentativa não autorizada.

- **A3 — Falha na comunicação com API:**
  O sistema de catraca aplica a última decisão armazenada em cache ou bloqueia por segurança.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF03 — Performance
- RNF06 — Integração

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

## Diagrama de Fluxo da Atividade

![UC07_Atividade](uml/UC07_Atividade.png)

---

# UC08 — Consultar Horários de Aulas

## Especificação

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize os horários e as vagas disponíveis das aulas oferecidas pela academia.

### Pré-condições
- Aluno deve estar autenticado no sistema.

### Pós-condições
- Aluno visualiza a grade de aulas com informações de horário, modalidade, instrutor e vagas disponíveis.

### Fluxo Principal
1. O aluno acessa o módulo de aulas.
2. O sistema exibe a grade de horários com todas as aulas disponíveis.
3. O aluno pode filtrar por modalidade, dia da semana ou instrutor.
4. O sistema atualiza a exibição conforme os filtros aplicados.

### Fluxos Alternativos
- **A1 — Nenhuma aula disponível no filtro selecionado:**
  O sistema exibe mensagem informando ausência de aulas para os critérios selecionados.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas

## Diagrama de Fluxo da Atividade

![UC08_Atividade](uml/UC08_Atividade.png)

---

# UC09 — Agendar Aula

## Especificação

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em uma aula disponível.

### Pré-condições
- Aluno deve estar autenticado no sistema.
- Aluno deve estar regular (mensalidade em dia).
- A aula deve possuir vagas disponíveis.

### Pós-condições
- Reserva confirmada e registrada no sistema.
- Notificação de confirmação enviada ao aluno.

### Fluxo Principal
1. O aluno consulta a grade de horários (UC08).
2. O aluno seleciona a aula desejada.
3. O sistema verifica a disponibilidade de vagas.
4. O sistema verifica a regularidade do aluno.
5. O sistema registra a reserva.
6. O sistema envia notificação de confirmação ao aluno.

### Fluxos Alternativos
- **A1 — Aula sem vagas:**
  O sistema exibe mensagem informando que a aula está lotada e não permite o agendamento.

- **A2 — Aluno inadimplente:**
  O sistema bloqueia o agendamento e orienta o aluno a regularizar a situação.

- **A3 — Aluno já possui reserva na mesma aula:**
  O sistema exibe mensagem de duplicidade e impede novo agendamento.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas
- RN01 — Bloqueio por inadimplência

## Diagrama de Fluxo da Atividade

![UC09_Atividade](uml/UC09_Atividade.png)

---

# UC10 — Cancelar Agendamento de Aula

## Especificação

### Ator Principal
Aluno

### Objetivo
Cancelar uma reserva de aula previamente agendada.

### Pré-condições
- Aluno deve estar autenticado no sistema.
- O agendamento deve existir e o cancelamento deve ser feito com no mínimo 1 hora de antecedência.

### Pós-condições
- Reserva cancelada e vaga liberada para outros alunos.

### Fluxo Principal
1. O aluno acessa seus agendamentos.
2. O sistema exibe a lista de reservas ativas do aluno.
3. O aluno seleciona o agendamento que deseja cancelar.
4. O sistema verifica se o cancelamento respeita o prazo mínimo de 1 hora.
5. O sistema cancela a reserva e libera a vaga.
6. O sistema confirma o cancelamento ao aluno.

### Fluxos Alternativos
- **A1 — Cancelamento fora do prazo:**
  O sistema informa que o cancelamento não é mais permitido pois a aula inicia em menos de 1 hora.

- **A2 — Nenhum agendamento ativo:**
  O sistema exibe mensagem informando que não há reservas para cancelar.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN03 — Cancelamento de agendamento

## Diagrama de Fluxo da Atividade

![UC10_Atividade](uml/UC10_Atividade.png)

---

# UC11 — Registrar Presença em Aula

## Especificação

### Ator Principal
Instrutor

### Objetivo
Registrar a presença dos alunos em uma aula ministrada.

### Pré-condições
- Instrutor deve estar autenticado no sistema.
- A aula deve estar agendada para o horário atual.

### Pós-condições
- Presença dos alunos registrada no sistema.

### Fluxo Principal
1. O instrutor acessa o módulo de aulas do dia.
2. O sistema exibe a lista de aulas do instrutor no dia corrente.
3. O instrutor seleciona a aula em andamento.
4. O sistema exibe a lista de alunos agendados para a aula.
5. O instrutor marca a presença de cada aluno.
6. O instrutor confirma o registro de presença.
7. O sistema salva as informações e exibe confirmação.

### Fluxos Alternativos
- **A1 — Aluno presente, mas sem agendamento:**
  O instrutor pode registrar a presença de alunos não previamente agendados, se houver vaga.

- **A2 — Nenhum agendamento na aula:**
  O sistema exibe mensagem informando que não há alunos agendados para a aula selecionada.

### RF Relacionados
- RF07 — Lista de Presença

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC11_Atividade](uml/UC11_Atividade.png)

---

# UC12 — Registrar Avaliação Física

## Especificação

### Ator Principal
Instrutor

### Objetivo
Registrar os dados de avaliação física de um aluno, incluindo medidas corporais e observações.

### Pré-condições
- Instrutor deve estar autenticado no sistema.
- O aluno deve estar ativo e com mensalidade regular.

### Pós-condições
- Avaliação física registrada e vinculada ao histórico do aluno.
- Notificação de nova avaliação enviada ao aluno.

### Fluxo Principal
1. O instrutor busca o aluno pelo nome ou CPF.
2. O sistema exibe os dados do aluno e seu histórico de avaliações.
3. O instrutor preenche os dados da avaliação: peso, altura, IMC, percentual de gordura e observações.
4. O instrutor pode anexar arquivos (imagens ou laudos).
5. O sistema salva a avaliação e vincula ao histórico do aluno.
6. O sistema notifica o aluno sobre a nova avaliação disponível.

### Fluxos Alternativos
- **A1 — Aluno inadimplente:**
  O sistema bloqueia o registro de avaliação e orienta o instrutor.

- **A2 — Arquivo inválido para anexo:**
  O sistema rejeita o arquivo e informa os formatos aceitos.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC12_Atividade](uml/UC12_Atividade.png)

---

# UC13 — Visualizar Histórico de Avaliações Físicas

## Especificação

### Ator Principal
Aluno, Instrutor

### Objetivo
Consultar o histórico de avaliações físicas de um aluno ao longo do tempo.

### Pré-condições
- Usuário deve estar autenticado no sistema.
- O aluno deve possuir ao menos uma avaliação cadastrada.

### Pós-condições
- Histórico de avaliações exibido com evolução dos dados ao longo do tempo.

### Fluxo Principal
1. O usuário acessa o módulo de avaliações físicas.
2. O sistema exibe a lista de avaliações do aluno em ordem cronológica.
3. O usuário pode selecionar uma avaliação para ver os detalhes completos.
4. O sistema exibe um gráfico de evolução das principais métricas (peso, IMC, % gordura).

### Fluxos Alternativos
- **A1 — Nenhuma avaliação cadastrada:**
  O sistema exibe mensagem informando ausência de avaliações no histórico.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC13_Atividade](uml/UC13_Atividade.png)

---

# UC14 — Emitir Relatório de Inadimplência

## Especificação

### Ator Principal
Gerente

### Objetivo
Gerar relatório com a lista de alunos inadimplentes, valores em aberto e tempo de atraso.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de inadimplência gerado, exibido e disponível para exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de inadimplência.
3. O gerente define o período e os filtros desejados (ex.: unidade, plano).
4. O sistema processa os dados e gera o relatório.
5. O sistema exibe o relatório com nome do aluno, dias em atraso e valor devido.
6. O gerente pode exportar o relatório em PDF ou CSV.

### Fluxos Alternativos
- **A1 — Nenhum aluno inadimplente no período:**
  O sistema exibe mensagem informando ausência de inadimplência no período selecionado.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF05 — Escalabilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC14_Atividade](uml/UC14_Atividade.png)

---

# UC15 — Emitir Relatório de Alunos Ativos

## Especificação

### Ator Principal
Gerente

### Objetivo
Gerar relatório com todos os alunos com matrícula ativa na academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de alunos ativos gerado e disponível para exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de alunos ativos.
3. O gerente define filtros opcionais (plano, período de matrícula, faixa etária).
4. O sistema gera o relatório com nome, plano, data de matrícula e situação.
5. O gerente pode exportar o relatório em PDF ou CSV.

### Fluxos Alternativos
- **A1 — Nenhum aluno ativo no filtro selecionado:**
  O sistema exibe mensagem informando ausência de resultados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC15_Atividade](uml/UC15_Atividade.png)

---

# UC16 — Emitir Relatório de Histórico de Acessos

## Especificação

### Ator Principal
Gerente

### Objetivo
Gerar relatório com o histórico de entradas dos alunos na academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de acessos gerado com datas, horários e identificação de cada aluno.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de histórico de acessos.
3. O gerente define o período e os filtros desejados (aluno específico, turno, unidade).
4. O sistema processa os dados de acesso registrados pela catraca.
5. O sistema exibe o relatório com data, horário e nome do aluno.
6. O gerente pode exportar o relatório em PDF ou CSV.

### Fluxos Alternativos
- **A1 — Nenhum acesso registrado no período:**
  O sistema exibe mensagem informando ausência de registros.

### RF Relacionados
- RF05 — Controle de Acesso
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC16_Atividade](uml/UC16_Atividade.png)

---

# UC17 — Emitir Relatório de Ocupação das Aulas

## Especificação

### Ator Principal
Gerente

### Objetivo
Gerar relatório com a taxa de ocupação das aulas oferecidas pela academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de ocupação gerado com percentual de preenchimento por aula.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de ocupação das aulas.
3. O gerente define o período e os filtros (modalidade, instrutor, turno).
4. O sistema calcula a taxa de ocupação por aula (agendados / capacidade máxima).
5. O sistema exibe o relatório com nome da aula, capacidade, agendamentos e percentual.
6. O gerente pode exportar o relatório em PDF ou CSV.

### Fluxos Alternativos
- **A1 — Nenhuma aula no período selecionado:**
  O sistema exibe mensagem informando ausência de dados para os filtros aplicados.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF05 — Escalabilidade

### RN Relacionadas
- RN02 — Limite de vagas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC17_Atividade](uml/UC17_Atividade.png)

---

# UC18 — Enviar Notificação de Vencimento de Mensalidade

## Especificação

### Ator Principal
Sistema

### Objetivo
Enviar notificações automáticas aos alunos informando sobre o vencimento próximo da mensalidade.

### Pré-condições
- O sistema deve estar em operação.
- O aluno deve possuir e-mail ou contato cadastrado.

### Pós-condições
- Notificação enviada ao aluno com informações sobre o vencimento.

### Fluxo Principal
1. O sistema executa a rotina automática de verificação de vencimentos.
2. O sistema identifica os alunos com mensalidade vencendo nos próximos 5 dias.
3. O sistema gera a notificação personalizada com nome do aluno, data de vencimento e valor.
4. O sistema envia a notificação por e-mail e/ou SMS.
5. O sistema registra o envio da notificação no histórico do aluno.

### Fluxos Alternativos
- **A1 — Falha no envio da notificação:**
  O sistema registra a falha e agenda nova tentativa de envio. Alerta o gerente em caso de falha persistente.

- **A2 — Aluno sem e-mail ou contato cadastrado:**
  O sistema ignora o envio e registra a inconsistência para revisão pela recepção.

### RF Relacionados
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

## Diagrama de Fluxo da Atividade

![UC18_Atividade](uml/UC18_Atividade.png)

---

# UC19 — Gerar Boleto / Token de Pagamento Online

## Especificação

### Ator Principal
Recepcionista, Sistema

### Objetivo
Gerar boleto bancário ou token de pagamento online para que o aluno quite sua mensalidade remotamente.

### Pré-condições
- O aluno deve estar cadastrado no sistema.
- O plano do aluno deve estar ativo.

### Pós-condições
- Boleto ou token de pagamento gerado e enviado ao aluno.
- Pagamento pendente registrado no sistema aguardando confirmação.

### Fluxo Principal
1. A recepcionista acessa o cadastro do aluno ou o sistema inicia o processo automaticamente.
2. O sistema verifica o valor da mensalidade em aberto.
3. O sistema aciona a integração com o gateway de pagamento.
4. O gateway retorna o boleto ou token de pagamento.
5. O sistema envia o boleto/token ao aluno por e-mail.
6. O sistema registra o pagamento como pendente.

### Fluxos Alternativos
- **A1 — Falha na comunicação com o gateway:**
  O sistema exibe mensagem de erro e orienta tentativa manual na recepção.

- **A2 — Aluno sem e-mail cadastrado:**
  O sistema exibe o boleto/token na tela para que a recepcionista realize o procedimento presencialmente.

### RF Relacionados
- RF03 — Controle de Pagamentos

### RNF Relacionados
- RNF02 — Segurança
- RNF06 — Integração

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade

## Diagrama de Fluxo da Atividade

![UC19_Atividade](uml/UC19_Atividade.png)

---

# UC20 — Gerenciar Usuários e Perfis de Acesso

## Especificação

### Ator Principal
Gerente

### Objetivo
Criar, editar, ativar e desativar contas de usuários do sistema, definindo perfis de acesso.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Usuário criado, atualizado ou com status alterado no sistema.
- Permissões de acesso aplicadas conforme o perfil definido.

### Fluxo Principal
1. O gerente acessa o módulo de gerenciamento de usuários.
2. O gerente seleciona a ação: criar, editar, ativar ou desativar usuário.
3. Para criar/editar: o gerente preenche nome, e-mail e perfil (Recepcionista, Instrutor ou Gerente).
4. O sistema valida as informações e verifica duplicidade de e-mail.
5. O sistema aplica as permissões correspondentes ao perfil selecionado.
6. O sistema salva as informações e envia credenciais ao novo usuário (em caso de criação).

### Fluxos Alternativos
- **A1 — E-mail já cadastrado:**
  O sistema exibe mensagem de duplicidade e impede o cadastro.

- **A2 — Tentativa de excluir o próprio usuário:**
  O sistema impede a exclusão e exibe mensagem de restrição.

- **A3 — Usuário desativado tenta fazer login:**
  O sistema bloqueia o acesso e orienta o usuário a contatar o gerente.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## Diagrama de Fluxo da Atividade

![UC20_Atividade](uml/UC20_Atividade.png)

---

## Considerações Finais

Este documento apresenta a especificação completa dos 20 casos de uso do Sistema FitPass Gym Management, acompanhados de diagramas de atividade detalhados com referência a arquivos PNG. Cada caso de uso descreve:

- **Ator Principal:** Quem realiza a ação
- **Objetivo:** O propósito do caso de uso
- **Pré-condições:** O que deve ser verdadeiro antes da execução
- **Pós-condições:** O resultado esperado após a conclusão
- **Fluxo Principal:** O caminho feliz do caso de uso
- **Fluxos Alternativos:** Tratamento de exceções e situações especiais
- **Relacionamentos:** Com requisitos funcionais, não-funcionais e regras de negócio
- **Diagrama de Fluxo da Atividade:** Visualização gráfica do fluxo de processo

Os diagramas de atividade seguem a notação padrão de diagramas de atividade UML e estão referenciados como imagens PNG, facilitando a compreensão e implementação do sistema pelos desenvolvedores.

---

**Data de Elaboração:** 18 de Março de 2026  
**Autores:** João Augusto de Freitas e Isadora Cabral dos Santos  
**Disciplina:** Engenharia de Software
