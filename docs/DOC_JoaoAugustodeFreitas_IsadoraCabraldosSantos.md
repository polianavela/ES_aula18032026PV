# Documento de Casos de Uso com Diagramas de Atividade
## Sistema FitPass Gym Management

**Alunos:** João Augusto de Freitas e Isadora Cabral dos Santos  

[Diagramas  e Casos de Uso (Aula 11-03)](https://github.com/maxvallim-coder/ES_aula11032026/blob/main/docs/UC_IsadoraCabraldosSantos_JoaoAugustodeFreitas.md)

---

## Índice
[Casos de Uso e Diagramas de Atividade](#casos-de-uso)
   - Diagrama geral de casos de uso
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

<img width="4096" height="486" alt="DUC_GERAL" src="https://github.com/user-attachments/assets/ef0f0f0a-da17-4875-a699-95f0909a6d3b" />

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

<img width="1020" height="653" alt="UC01_Atividade" src="https://github.com/user-attachments/assets/edefae24-e41a-4bc3-9240-09043a53bb8b" />

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

<img width="327" height="1221" alt="UC02_Atividade" src="https://github.com/user-attachments/assets/1e2d15aa-bc6d-4ab7-84cc-e17bafde60d7" />

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

<img width="355" height="896" alt="UC03_Atividade" src="https://github.com/user-attachments/assets/26a08e7b-eb21-4dc8-adbb-b1802c9ed89b" />

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

<img width="750" height="712" alt="UC04_Atividade" src="https://github.com/user-attachments/assets/acb05e3f-b2b8-44f8-9d8f-0d495d8390c4" />

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

<img width="515" height="1126" alt="UC05_Atividade" src="https://github.com/user-attachments/assets/0ee39d84-2007-410f-9119-0470ffce1dea" />

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

<img width="557" height="959" alt="UC06_Atividade" src="https://github.com/user-attachments/assets/c42c1c8a-9f6d-4b17-b105-672806202dd0" />

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

<img width="1082" height="802" alt="UC07_Atividade" src="https://github.com/user-attachments/assets/4c07fb4a-5629-497e-91eb-f2ca974f930d" />

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

<img width="574" height="737" alt="UC08_Atividade" src="https://github.com/user-attachments/assets/b4679766-ee0d-4c61-9f05-0e84a3634a4c" />

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

<img width="286" height="1280" alt="UC09_Atividade" src="https://github.com/user-attachments/assets/78c9f7bc-5a96-49c7-8de7-7fda27cb5748" />

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

<img width="718" height="892" alt="UC10_Atividade" src="https://github.com/user-attachments/assets/5137c95d-5c13-4d0e-9512-b8c941e98126" />

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

<img width="424" height="1001" alt="UC11_Atividade" src="https://github.com/user-attachments/assets/aa138d7f-be75-4e85-9c33-e1cb89754e9c" />

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

<img width="405" height="1374" alt="UC12_Atividade" src="https://github.com/user-attachments/assets/f8923ca3-faf5-4192-b636-3016d9b02f84" />

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

<img width="421" height="1119" alt="UC13_Atividade" src="https://github.com/user-attachments/assets/46605918-8bec-45c0-88d5-d59e458f7e32" />

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

<img width="475" height="1099" alt="UC14_Atividade" src="https://github.com/user-attachments/assets/0644eb1c-f7b4-49bc-be9e-b5d67a96d526" />

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

<img width="537" height="937" alt="UC15_Atividade" src="https://github.com/user-attachments/assets/f7588144-5a26-4476-be10-d00ee9cfa9fc" />

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

<img width="463" height="937" alt="UC16_Atividade" src="https://github.com/user-attachments/assets/31b8316d-4e65-4edc-9452-c0847f2e8abb" />

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

<img width="533" height="1153" alt="UC17_Atividade" src="https://github.com/user-attachments/assets/b395ee42-2f5b-42c0-b1c2-77f74758b8cf" />

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

<img width="682" height="1343" alt="UC18_Atividade" src="https://github.com/user-attachments/assets/dd0554b2-5268-4423-bd77-00f88793f8b5" />

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

<img width="548" height="1281" alt="UC19_Atividade" src="https://github.com/user-attachments/assets/bda9f871-8b5f-470f-b5a0-254888adefce" />

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

<img width="792" height="1114" alt="UC20_Atividade" src="https://github.com/user-attachments/assets/9f54abf4-6d25-49ad-a636-f5d7bc89fad4" />

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
