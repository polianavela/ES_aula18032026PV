### UC01 — Realizar Login
**Ator Principal:** Recepcionista, Instrutor, Gerente, Aluno
**Objetivo:** Permitir que os usuários acessem o sistema com seus respectivos perfis.
**Pré-condições:** O usuário deve possuir um cadastro ativo no sistema.
**Pós-condições:** Sessão iniciada com sucesso e funcionalidades restritas ao perfil liberadas.

**Fluxo Principal:**
1. O usuário acessa a tela de login.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais e o perfil do usuário.
4. O sistema autentica o usuário e o redireciona para o painel correspondente ao seu perfil.

**Fluxos Alternativos:**
- **A1 — Credenciais inválidas:** O sistema exibe mensagem de erro e solicita nova digitação.
- **A2 — Cadastro inativo:** O sistema informa que a conta está desativada e orienta a buscar a recepção.

**RF Relacionados:** RF01, RF02, RF07, RF09
**RNF Relacionados:** RNF02, RNF03, RNF04
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC01

<img width="551" height="431" alt="image" src="https://github.com/user-attachments/assets/c8e13e28-e732-4ca2-b13a-0fa0f1d922cc" />

---

### UC02 — Cadastrar Novo Aluno
**Ator Principal:** Recepcionista
**Objetivo:** Registrar um novo aluno no sistema.
**Pré-condições:** A recepcionista deve estar logada no sistema.
**Pós-condições:** Novo aluno cadastrado e apto a contratar um plano.

**Fluxo Principal:**
1. A recepcionista acessa a opção de cadastro de alunos.
2. A recepcionista insere os dados pessoais, contato e endereço do aluno.
3. O sistema valida os dados inseridos.
4. O sistema salva o registro e gera o ID do aluno.

**Fluxos Alternativos:**
- **A1 — CPF já cadastrado:** O sistema alerta que o aluno já existe e sugere ir para a tela de edição.
- **A2 — Dados incompletos:** O sistema destaca os campos obrigatórios e impede o salvamento.

**RF Relacionados:** RF01
**RNF Relacionados:** RNF02, RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC02

<img width="508" height="446" alt="image" src="https://github.com/user-attachments/assets/327c15e5-027a-4cff-be59-85c243786c3b" />

---

### UC03 — Vincular Plano ao Aluno
**Ator Principal:** Recepcionista
**Objetivo:** Associar um plano contratado ao cadastro do aluno.
**Pré-condições:** O aluno deve estar previamente cadastrado no sistema.
**Pós-condições:** Aluno vinculado a um plano com datas de vigência estabelecidas.

**Fluxo Principal:**
1. A recepcionista seleciona o aluno desejado.
2. A recepcionista escolhe o plano a ser contratado (mensal, anual, et cetera...)
3. O sistema calcula a data de vencimento com base no plano.
4. O sistema salva o vínculo e aguarda o pagamento.

**Fluxos Alternativos:**
- **A1 — Aluno já possui plano ativo:** O sistema questiona se é um upgrade ou substituição de plano.

**RF Relacionados:** RF01, RF02
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC03

<img width="324" height="541" alt="image" src="https://github.com/user-attachments/assets/594e279e-bcaa-4a40-9c29-de25fc0418e5" />

---

### UC04 — Criar Tipo de Plano
**Ator Principal:** Gerente
**Objetivo:** Cadastrar novas modalidades de planos oferecidos pela academia.
**Pré-condições:** O gerente deve estar logado no sistema.
**Pós-condições:** Novo plano disponível para comercialização

**Fluxo Principal:**
1. O gerente acessa a área de gerenciamento de planos.
2. O gerente clica em criar novo plano.
3. O gerente insere nome, duração e valor.
4. O sistema salva o novo plano como ativo.

**Fluxos Alternativos:**
- **A1 — Nome de plano duplicado:** O sistema avisa que já existe um plano com esse nome e pede alteração.

**RF Relacionados:** RF02
**RNF Relacionados:** RNF03, RNF04
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC04

<img width="310" height="422" alt="image" src="https://github.com/user-attachments/assets/86885e9d-a81c-48d4-9bb1-5d3548273d16" />


---

### UC05 — Editar Tipo de Plano
**Ator Principal:** Gerente
**Objetivo:** Modificar características ou valores de um plano existente.
**Pré-condições:** O plano deve existir no sistema.
**Pós-condições:** Plano atualizado sem afetar os contratos já vigentes.

**Fluxo Principal:**
1. O gerente seleciona um plano existente.
2. O gerente altera as informações desejadas (ex: reajuste de valor).
3. O sistema questiona se a alteração se aplica a renovações futuras.
4. O sistema salva as edições.

**Fluxos Alternativos:**
- **A1 — Cancelamento da edição:** O gerente clica em cancelar e o sistema descarta as alterações.

**RF Relacionados:** RF02
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC05

<img width="393" height="367" alt="image" src="https://github.com/user-attachments/assets/94ddeeea-d98d-42b3-a31d-156493bef3ae" />

---

### UC06 — Ativar/Desativar Plano
**Ator Principal:** Gerente
**Objetivo:** Controlar a disponibilidade de planos para novas vendas.
**Pré-condições:** O plano deve estar cadastrado no sistema.
**Pós-condições:** Status do plano alterado (Ativo/Inativo).

**Fluxo Principal:**
1. O gerente lista os planos cadastrados.
2. O gerente clica no botão de alternar status de um plano específico.
3. O sistema confirma a ação e atualiza o status.

**Fluxos Alternativos:**
- **A1 — Desativar plano com alunos ativos:** O sistema alerta que o plano será descontinuado apenas para novas vendas, mantendo os atuais até o fim do contrato.

**RF Relacionados:** RF02
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC06

<img width="290" height="451" alt="image" src="https://github.com/user-attachments/assets/b9035764-0028-4bf5-843d-5ba410790ad7" />

---

### UC07 — Registrar Pagamento na Recepção
**Ator Principal:** Recepcionista
**Objetivo:** Dar baixa na mensalidade através de pagamento presencial.
**Pré-condições:** O aluno deve ter uma cobrança pendente.
**Pós-condições:** Mensalidade quitada e status do aluno atualizado.

**Fluxo Principal:**
1. A recepcionista localiza o cadastro do aluno.
2. A recepcionista seleciona a fatura em aberto.
3. A recepcionista informa a forma de pagamento (dinheiro, cartão ou PIX).
4. O sistema registra o pagamento no valor integral.
5. O sistema atualiza imediatamente a regularidade do aluno.

**Fluxos Alternativos:**
- **A1 — Tentativa de pagamento parcial:** O sistema bloqueia a ação informando que o valor deve ser integral, conforme regra de negócio.

**RF Relacionados:** RF03, RF04
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN04, RN06, RN07

#### Diagrama de Atividade - UC07

<img width="455" height="422" alt="image" src="https://github.com/user-attachments/assets/670bd04e-b893-459b-857b-2457a56c4fb8" />

---

### UC08 — Gerar Boleto/Link para Pagamento Online
**Ator Principal:** Aluno
**Objetivo:** Permitir o pagamento online da mensalidade.
**Pré-condições:** Aluno com fatura gerada no sistema.
**Pós-condições:** Boleto ou link de cartão gerado e disponibilizado para pagamento.

**Fluxo Principal:**
1. O aluno acessa a área financeira no aplicativo.
2. O aluno seleciona a fatura pendente.
3. O aluno escolhe a opção de pagamento online.
4. O sistema gera o boleto ou a interface de pagamento via cartão.

**Fluxos Alternativos:**
- **A1 — Falha na comunicação com portal de pagamento:** O sistema exibe mensagem de erro e orienta a tentar novamente mais tarde.

**RF Relacionados:** RF03
**RNF Relacionados:** RNF02, RNF04
**RN Relacionadas:** RN04

#### Diagrama de Atividade - UC08

<img width="395" height="367" alt="image" src="https://github.com/user-attachments/assets/fb262b9d-6656-4da0-a13a-3dbd915374f6" />

---

### UC09 — Verificar Regularidade do Aluno
**Ator Principal:** Sistema
**Objetivo:** Analisar automatically se o aluno está com a mensalidade em dia.
**Pré-condições:** Sistema em operação normal processando rotinas diárias.
**Pós-condições:** Status do aluno atualizado (Regular ou Inadimplente).

**Fluxo Principal:**
1. O sistema verifica a data de vencimento da mensalidade de todos os alunos.
2. O sistema compara a data de vencimento com a data atual.
3. Se a mensalidade estiver vencida, o sistema altera o status do aluno para inadimplente.

**Fluxos Alternativos:**
- **A1 — Mensalidade paga ou no prazo:** O sistema mantém o status do aluno como regular e não realiza alterações.

**RF Relacionados:** RF04
**RNF Relacionados:** RNF01, RNF03
**RN Relacionadas:** RN01, RN07

#### Diagrama de Atividade - UC09

<img width="410" height="312" alt="image" src="https://github.com/user-attachments/assets/f2ed4388-2db7-41ab-a250-c54755b80f5e" />

---

### UC10 — Validar Acesso na Catraca
**Ator Principal:** Sistema de Catraca (API Externa), Aluno
**Objetivo:** Controlar a entrada do aluno na academia utilizando a tecnologia RFID.
**Pré-condições:** O aluno deve aproximar sua tag RFID do leitor da catraca.
**Pós-condições:** Catraca liberada ou bloqueada, com o devido registro de acesso salvo no histórico.

**Fluxo Principal:**
1. O aluno aproxima o RFID da catraca.
2. A catraca envia o ID do aluno via API REST JSON para o sistema central.
3. O sistema verifica a regularidade do aluno.
4. O aluno estando regular, o sistema envia o comando de liberação.
5. A catraca é destravada e o acesso é registrado com sucesso.

**Fluxos Alternativos:**
- **A1 — Aluno inadimplente há mais de 5 dias:** O sistema retorna comando de bloqueio. A catraca não abre e exibe um aviso de pendência financeira.
- **A2 — Falha na comunicação via API:** A catraca não consegue contatar o servidor e alerta a recepção para validação manual.

**RF Relacionados:** RF04, RF05, RF09
**RNF Relacionados:** RNF01, RNF03, RNF06
**RN Relacionadas:** RN01

#### Diagrama de Atividade - UC10

<img width="648" height="541" alt="image" src="https://github.com/user-attachments/assets/02204054-67dc-4f25-bcdf-f2c60beca76d" />

---

### UC11 — Visualizar Horários de Aulas
**Ator Principal:** Aluno
**Objetivo:** Consultar a grade de aulas disponíveis na academia e seus respectivos horários.
**Pré-condições:** O aluno deve estar logado na sua conta.
**Pós-condições:** Grade de horários exibida corretamente na tela.

**Fluxo Principal:**
1. O aluno navega até a seção de agendamento de aulas.
2. O sistema carrega e exibe a lista de aulas cadastradas para a semana.
3. O aluno visualiza os horários, os instrutores responsáveis e o número de vagas.

**Fluxos Alternativos:**
- **A1 — Nenhuma aula agendada para o período:** O sistema exibe uma mensagem informando que não há aulas programadas.

**RF Relacionados:** RF06
**RNF Relacionados:** RNF04
**RN Relacionadas:** Nenhuma

#### Diagrama de Atividade - UC11

<img width="463" height="312" alt="image" src="https://github.com/user-attachments/assets/eccb1bc5-8fe3-4c86-846e-9144469b0551" />

---

### UC12 — Reservar Vaga em Aula
**Ator Principal:** Aluno
**Objetivo:** Garantir a participação em uma aula específica ofertada pela academia.
**Pré-condições:** O aluno deve estar regularizado e a aula desejada deve possuir vagas disponíveis.
**Pós-condições:** Vaga reservada para o aluno e contabilizada no limite da aula.

**Fluxo Principal:**
1. O aluno seleciona a aula desejada na grade de horários.
2. O aluno aciona a opção de confirmar reserva.
3. O sistema verifica se o limite máximo de alunos para a aula já foi atingido.
4. O sistema confirma a reserva e subtrai uma vaga do total disponível.

**Fluxos Alternativos:**
- **A1 — Limite de vagas já atingido:** O sistema impede o agendamento e avisa que a turma está lotada.
- **A2 — Aluno inadimplente:** O sistema bloqueia a reserva e solicita que o aluno regularize sua situação financeira.

**RF Relacionados:** RF06, RF10
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN02

#### Diagrama de Atividade - UC12

<img width="490" height="446" alt="image" src="https://github.com/user-attachments/assets/b27c8e25-520e-456f-b1e5-59d1e4462ed2" />

---

### UC13 — Cancelar Reserva de Aula
**Ator Principal:** Aluno
**Objetivo:** Permitir que o aluno desista de uma reserva de aula feita anteriormente.
**Pré-condições:** O aluno deve ter uma reserva ativa registrada no sistema.
**Pós-condições:** Reserva cancelada com sucesso e a vaga restituída ao sistema para outros alunos.

**Fluxo Principal:**
1. O aluno acessa a área de suas reservas ativas.
2. O aluno seleciona a aula específica e escolhe a opção de cancelamento.
3. O sistema verifica o tempo restante para o início programado da aula.
4. Sendo o tempo superior a 1 hora, o sistema efetua o cancelamento e libera a vaga.

**Fluxos Alternativos:**
- **A1 — Cancelamento fora do prazo estipulado:** O tempo restante é menor que 1 hora. O sistema bloqueia a ação, informando a regra de negócio que impede o cancelamento em cima da hora.

**RF Relacionados:** RF06
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN03

#### Diagrama de Atividade - UC13

<img width="330" height="422" alt="image" src="https://github.com/user-attachments/assets/89144f72-a592-4215-87cc-426272ff30ab" />

---

### UC14 — Registrar Presença na Aula
**Ator Principal:** Instrutor
**Objetivo:** Confirmar e registrar o comparecimento dos alunos que reservaram a respectiva aula.
**Pré-condições:** O instrutor deve estar logado e a aula deve estar em seu horário de início ou já finalizada.
**Pós-condições:** Lista de presença salva e armazenada no banco de dados do sistema.

**Fluxo Principal:**
1. O instrutor acessa o painel da aula sob sua responsabilidade.
2. O sistema exibe a listagem completa de alunos com reserva confirmada.
3. O instrutor marca a presença ou a ausência de cada aluno da lista.
4. O sistema salva as informações de frequência.

**Fluxos Alternativos:**
- **A1 — Aluno presente sem reserva prévia:** O instrutor tenta adicionar o aluno manualmente na hora. O sistema verifica se ainda há vagas na aula e autoriza o registro.

**RF Relacionados:** RF07
**RNF Relacionados:** RNF04
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC14

<img width="361" height="515" alt="image" src="https://github.com/user-attachments/assets/ef20e8a3-87bf-4b60-84e7-8b58403d4c50" />

---

### UC15 — Registrar Avaliação Física
**Ator Principal:** Instrutor
**Objetivo:** Lançar dados biométricos, medidas e métricas de desempenho do aluno no sistema.
**Pré-condições:** O instrutor deve estar logado e o aluno avaliado deve possuir status ativo e regular.
**Pós-condições:** Avaliação física salva no histórico do aluno.

**Fluxo Principal:**
1. O instrutor acessa o perfil do aluno no sistema.
2. O instrutor clica na opção para iniciar uma nova avaliação física.
3. O sistema verifica a regularidade financeira do aluno.
4. O instrutor insere os dados coletados (peso, IMC, percentual de gordura, etc.).
5. O sistema salva a avaliação e notifica o aluno sobre a disponibilidade dos resultados.

**Fluxos Alternativos:**
- **A1 — Aluno em situação irregular:** O sistema bloqueia a criação da avaliação e exibe um alerta de que o procedimento só é permitido para alunos com mensalidade em dia.

**RF Relacionados:** RF08, RF10
**RNF Relacionados:** RNF02, RNF03
**RN Relacionadas:** RN05, RN06

#### Diagrama de Atividade - UC15

<img width="374" height="477" alt="image" src="https://github.com/user-attachments/assets/8ed19163-80b6-4a0d-a933-8225fa10b37f" />

---

### UC16 — Anexar Arquivo à Avaliação Física
**Ator Principal:** Instrutor
**Objetivo:** Permitir a adição de documentos complementares (fotos, exames médicos) a uma avaliação física.
**Pré-condições:** O instrutor deve estar com a tela de registro ou edição de uma avaliação física aberta.
**Pós-condições:** Arquivo armazenado e devidamente vinculado à avaliação específica do aluno.

**Fluxo Principal:**
1. O instrutor clica no botão destinado a anexar arquivos.
2. O instrutor seleciona o arquivo desejado em seu dispositivo.
3. O sistema realiza o upload e aplica a criptografia necessária.
4. O sistema vincula o documento à avaliação que está sendo salva.

**Fluxos Alternativos:**
- **A1 — Formato de arquivo não suportado:** O sistema rejeita o upload e exibe uma mensagem informando quais são os formatos válidos.

**RF Relacionados:** RF08
**RNF Relacionados:** RNF02, RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC16

<img width="311" height="422" alt="image" src="https://github.com/user-attachments/assets/55e9f536-5e42-4414-a4d8-7f6f444ea9c6" />

---

### UC17 — Emitir Relatório de Inadimplência
**Ator Principal:** Gerente
**Objetivo:** Gerar e visualizar uma lista contendo todos os alunos que estão com pagamentos em atraso.
**Pré-condições:** O gerente deve estar autenticado no sistema.
**Pós-condições:** Relatório de inadimplentes exibido em tela para análise.

**Fluxo Principal:**
1. O gerente navega até o módulo de relatórios gerenciais.
2. O gerente seleciona a opção "Relatório de Inadimplência".
3. O sistema processa a busca cruzando alunos ativos com faturas vencidas.
4. O sistema exibe a listagem detalhando nomes, valores devidos e dias de atraso.

**Fluxos Alternativos:**
- **A1 — Nenhum aluno inadimplente encontrado:** O sistema exibe uma mensagem de sucesso: "Nenhum aluno inadimplente no momento".

**RF Relacionados:** RF09
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC17

<img width="328" height="367" alt="image" src="https://github.com/user-attachments/assets/1aed98df-989d-4d26-bf5d-c6445662cca8" />

---

### UC18 — Emitir Relatório de Alunos Ativos e Acessos
**Ator Principal:** Gerente
**Objetivo:** Acompanhar o volume da base de clientes ativos e o histórico do fluxo de entradas pela catraca.
**Pré-condições:** O gerente deve estar autenticado no sistema.
**Pós-condições:** Dados estatísticos de frequência e matrículas consolidados e exibidos.

**Fluxo Principal:**
1. O gerente seleciona a opção para gerar o relatório de acessos e alunos ativos.
2. O gerente define o intervalo de datas desejado para a análise.
3. O sistema consolida os logs gerados pela catraca e os cadastros regulares do período.
4. O sistema apresenta o relatório de forma estruturada.

**Fluxos Alternativos:**
- **A1 — Período de busca muito extenso:** O sistema informa que o volume de dados é muito grande e solicita que o gerente diminua o intervalo de datas para não comprometer a performance.

**RF Relacionados:** RF09
**RNF Relacionados:** RNF03, RNF05
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC18

<img width="404" height="367" alt="image" src="https://github.com/user-attachments/assets/dbdaf6bc-ecd2-4f01-9b07-917f70a55cc3" />

---

### UC19 — Emitir Relatório de Ocupação das Aulas
**Ator Principal:** Gerente
**Objetivo:** Analisar as taxas de ocupação das aulas ofertadas para auxiliar na tomada de decisão sobre a grade horária.
**Pré-condições:** O gerente deve estar autenticado no sistema.
**Pós-condições:** Relatório comparativo de vagas totais versus presenças gerado com sucesso.

**Fluxo Principal:**
1. O gerente acessa a funcionalidade de relatórios de ocupação de aulas.
2. O gerente aplica os filtros desejados (por modalidade, instrutor ou período).
3. O sistema calcula o cruzamento entre o total de vagas disponibilizadas e as presenças registradas.
4. O sistema exibe os resultados na tela de forma analítica.

**Fluxos Alternativos:**
- **A1 — Ocupação não registrada no período:** O sistema informa que não há dados de aulas finalizadas para os filtros selecionados.

**RF Relacionados:** RF09
**RNF Relacionados:** RNF03
**RN Relacionadas:** RN06

#### Diagrama de Atividade - UC19

<img width="353" height="367" alt="image" src="https://github.com/user-attachments/assets/1a81b8ca-6c4f-4792-92d5-2dd57eb5050b" />

---

### UC20 — Enviar Notificações Automáticas
**Ator Principal:** Sistema
**Objetivo:** Manter os alunos informados sobre eventos importantes relacionados às suas contas e atividades na academia.
**Pré-condições:** A ocorrência de um evento gatilho pré-definido (ex: vencimento de fatura, confirmação de aula, avaliação lançada).
**Pós-condições:** Mensagem padronizada disparada para os canais de contato do aluno.

**Fluxo Principal:**
1. O sistema identifica internamente que um evento gatilho ocorreu.
2. O sistema formata a mensagem correspondente ao tipo de evento.
3. O sistema recupera os dados de contato do aluno afetado.
4. O sistema realiza o disparo da notificação e salva a ação no log do sistema.

**Fluxos Alternativos:**
- **A1 — Falha no disparo da mensagem:** O sistema tenta o reenvio automático após um curto intervalo de tempo; se falhar novamente, salva o erro no log para verificação técnica.

**RF Relacionados:** RF10
**RNF Relacionados:** RNF01, RNF03
**RN Relacionadas:** Nenhuma

#### Diagrama de Atividade - UC20
<img width="418" height="541" alt="image" src="https://github.com/user-attachments/assets/338b7bd6-65f6-4c1d-80ac-10692ded0dd9" />
