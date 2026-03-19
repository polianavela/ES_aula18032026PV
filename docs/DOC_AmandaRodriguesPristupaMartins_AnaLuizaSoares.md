## UC01 — Realizar Login (UC EXEMPLO - FAZER DESSA FORMA PARA TODOS OS CASOS DE USO, NESSE MESMO DOCUMENTO)

### Ator Principal
Usuário

### Objetivo
Permitir que o usuário acesse o sistema.

### Pré-condições
- Usuário deve possuir cadastro ativo.

### Pós-condições
- Sessão iniciada com sucesso.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- RF01, RF02, RF09

### RNF Relacionados
- RNF01 (Segurança), RNF03 (Tempo de Resposta)

### RN Relacionadas
- RN06
<img width="560" height="299" alt="image" src="https://github.com/user-attachments/assets/1c90a815-f456-4f89-b7ef-b50aa450a3f6" />

--- 
## UC02 - Cadastrar Novo Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo cliente na base de dados da academia.

### Pré-condições
- Recepcionista autenticado no sistema.

### Pós-condições
_ Aluno registrado com dados pessoais, endereço e plano inicial vinculado.

### Fluxo Principal
1. A recepcionista acessa o módulo de matrículas.
2. O sistema solicita dados: Nome, CPF, Endereço, Contato e Plano.
3. A recepcionista preenche as informações.
4. O sistema valida os campos obrigatórios e salva o registro.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:**
   O sistema alerta que o aluno já existe e impede a duplicidade.

### RF Relacionados
RF01

### RNF Relacionados
RNF04 (Integridade de Dados)

### RN Relacionadas
RN06
<img width="389" height="422" alt="image" src="https://github.com/user-attachments/assets/3f3da5e1-cc91-4672-8e15-7ec82a65d036" />

---
## UC03 — Criar Novo Plano de Academia

### Ator Principal
Gerente

### Objetivo
Definir novas modalidades de planos (Mensal, Anual, etc.).

### Pré-condições
- Gerente autenticado no sistema.

### Pós-condições
- Novo tipo de plano disponível para venda nas matrículas.

### Fluxo Principal
1. O gerente acessa "Configurações de Planos".
2. O gerente define o nome, valor, duração e modalidades incluídas.
3. O sistema armazena a nova configuração.

### Fluxos Alternativos
- **A1 — Valor inválido:**
   O sistema solicita correção de valores negativos ou zerados.

### RF Relacionados
RF02

### RNF Relacionados
RNF05 (Escalabilidade)

### RN Relacionadas
RN06
<img width="430" height="367" alt="image" src="https://github.com/user-attachments/assets/a6e55ca4-3cec-42a5-a62d-28f545d6ae24" />

---
## UC04 — Editar Plano Existente

### Ator Principal
Gerente

### Objetivo
Alterar valores ou condições de um plano já cadastrado.

### Pré-condições
- Plano deve estar cadastrado no sistema.

### Pós-condições
- Dados do plano atualizados para novas vendas.

### Fluxo Principal
!. O gerente busca o plano desejado.
2. O sistema exibe os dados atuais.
3. O gerente altera as informações necessárias.
4. O sistema valida e salva as alterações.

### Fluxos Alternativos
- **A1 — Plano com alunos ativos:**
   O sistema avisa que a mudança afetará apenas novas adesões.

### RF Relacionados
RF02

### RNF Relacionados
RNF02 (Disponibilidade)

### RN Relacionadas
RN06
<img width="342" height="451" alt="image" src="https://github.com/user-attachments/assets/b1d61fb7-869d-44a1-a2ce-eefff8b6d630" />

---
## UC05 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Registrar a quitação de mensalidade realizada na recepção.

### Pré-condições
- Aluno selecionado e com débito pendente.

### Pós-condições
- Pagamento registrado e situação do aluno atualizada (RN07).
  
### Fluxo Principal
1. O recepcionista seleciona o aluno e a parcela.
2. O sistema solicita a forma de pagamento (Dinheiro, Cartão ou PIX).
3. O recepcionista confirma o recebimento do valor integral (RN04).
4. O sistema gera o comprovante e atualiza o status financeiro imediatamente.

### Fluxos Alternativos
- **A1 — Pagamento parcial:**
   O sistema bloqueia a operação informando a RN04.

### RF Relacionados
RF03, RF04

### RNF Relacionados
RNF03 (Tempo de Resposta)

### RN Relacionadas
RN04, RN06, RN07
<img width="488" height="367" alt="image" src="https://github.com/user-attachments/assets/7a65acbf-9047-4618-a666-43ac73f61280" />

---
## UC06 — Gerar Boleto para Pagamento Online

### Ator Principal
Recepcionista

### Objetivo
Emitir documento de cobrança para pagamento remoto.

### Pré-condições
- Integração financeira ativa.

### Pós-condições
- Boleto gerado e disponibilizado para o aluno.

### Fluxo Principal
1. O recepcionista solicita a emissão de cobrança para o aluno.
2. O sistema comunica-se com a API bancária.
3. O sistema gera o link do boleto e o salva no perfil do aluno.

### Fluxos Alternativos
- **A1 — Falha na API:**
- O sistema avisa sobre a indisponibilidade e sugere tentar mais tarde.

## RF Relacionados
RF03

## RNF Relacionados
RNF06 (Interoperabilidade)

## RN Relacionadas
RN06
<img width="367" height="367" alt="image" src="https://github.com/user-attachments/assets/a71d2979-769a-4f1c-9411-624c9eb4381c" />

---
## UC07 — Verificar Regularidade do Aluno (Automático)

### Ator Principal
Sistema

### Objetivo
Monitorar diariamente o status financeiro de todos os alunos.

### Pré-condições
- Rotina agendada ou gatilho de acesso.

### Pós-condições
- Status do aluno atualizado para "Inadimplente" ou "Regular".

### Fluxo Principal
1. O sistema verifica a data de vencimento das parcelas.
2. O sistema identifica alunos com pagamentos atrasados.
3. Se o atraso for superior a 5 dias, o sistema marca o aluno para bloqueio de acesso.

### Fluxos Alternativos
- **A1 — Pagamento identificado:**
- O sistema restaura a regularidade (RN07).

### RF Relacionados
RF04

### RNF Relacionados
RNF01 (Confiabilidade)

### RN Relacionadas
RN01, RN07
<img width="422" height="405" alt="image" src="https://github.com/user-attachments/assets/c19dd072-a69b-400e-b5aa-8f6492c6e337" />

---
## UC08 — Validar Acesso na Catraca

### Ator Principal
Sistema de Catraca (API)

### Objetivo
Liberar ou bloquear a entrada física do aluno via RFID.

### Pré-condições
- Aluno posiciona a tag RFID no leitor.

### Pós-condições
- Acesso permitido ou mensagem de bloqueio exibida.

### Fluxo Principal
1. O aluno aproxima o RFID.
2. O sistema de catraca envia o ID para o servidor FitPass.
3. O sistema verifica a regularidade (RF04).
4. Se o aluno estiver regular ou com atraso ≤ 5 dias, o sistema envia sinal de liberação.


### Fluxos Alternativos
- **A1 — Inadimplência > 5 dias:**
- O sistema nega o acesso (RN01) e instrui ir à recepção.

### RF Relacionados
RF04, RF05

### RNF Relacionados
RNF07 (Desempenho: < 1s)

### RN Relacionadas
RN01
<img width="353" height="422" alt="image" src="https://github.com/user-attachments/assets/d239fff6-bed8-4be4-a0b0-0d29c8bec645" />

---
## UC09 — Consultar Grade de Aulas

### Ator Principal
Aluno

### Objetivo
Visualizar horários e modalidades disponíveis.

### Pré-condições
- Aluno logado no aplicativo ou portal.

### Pós-condições
- Informações de horários exibidas ao usuário.

### Fluxo Principal
- O aluno acessa o módulo de "Agendamentos".
- O sistema exibe a lista de aulas, horários, instrutores e vagas disponíveis.

### Fluxos Alternativos
- **A1 — Nenhuma aula cadastrada:**
   O sistema informa que não há horários para a data.

### RF Relacionados
RF06

### RNF Relacionados
RNF08 (Usabilidade)

### RN Relacionadas
Nenhuma
<img width="440" height="374" alt="image" src="https://github.com/user-attachments/assets/30157622-249d-4962-85fb-6a3aa21513dc" />

---
### UC10 — Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em uma aula específica.

### Pré-condições
- Aluno deve estar regular e a aula deve ter vagas disponíveis.
  
### Pós-condições
- Reserva confirmada e vaga subtraída do total.

### Fluxo Principal
1. O aluno seleciona a aula desejada.
2. O sistema verifica o limite de vagas (RN02).
3. O sistema confirma a reserva e envia notificação (RF10).

### Fluxos Alternativos
- **A1 — Aula lotada:**
   O sistema informa que não há mais vagas e bloqueia a reserva.

### RF Relacionados
RF06, RF10

### RNF Relacionados
RNF04 (Consistência)

### RN Relacionadas
RN02
<img width="395" height="367" alt="image" src="https://github.com/user-attachments/assets/52ca880c-f10f-4036-88bf-6517137c4a89" />

---
## UC11 — Gerar Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Listar todos os alunos com matrículas vigentes para análise de retenção e faturamento.

### Pré-condições
- Gerente autenticado com permissões administrativas.

### Pós-condições
- Relatório gerado com sucesso contendo a lista de membros ativos.

### Fluxo Principal
1. O gerente acessa o menu "Relatórios Gerenciais".
2. O gerente seleciona a opção "Relatório de Alunos Ativos".
3. O sistema consulta a base de dados filtrando por alunos com planos ativos e situação financeira regular.
4. O sistema exibe a lista com Nome, Plano, Data de Expiração e Último Acesso.

### Fluxos Alternativos
- **A1 — Nenhum registro encontrado:**
   O sistema informa que não há alunos ativos na base de dados no momento.

### RF Relacionados
RF09

### RNF Relacionados
RNF10 (Geração de relatórios)

### RN Relacionadas
RN06   
<img width="456" height="312" alt="image" src="https://github.com/user-attachments/assets/3eeb23bf-941d-4599-81cd-24478b497f08" />

---
## UC12 — Cancelar Reserva de Aula

### Ator Principal
Aluno

### Objetivo
Desistir da participação em uma aula previamente agendada.

### Pré-condições
- Reserva ativa no sistema.

### Pós-condições
- Vaga liberada para outros alunos.

### Fluxo Principal
1.	O aluno solicita o cancelamento da reserva.
2.	O sistema verifica se o horário atual é pelo menos 1 hora antes da aula (RN03).
3.	O sistema confirma o cancelamento.

### Fluxos Alternativos
- **A1 — Fora do prazo:**
   O sistema impede o cancelamento via app por estar a menos de 1 hora do início.

### RF Relacionados
RF06

### RNF Relacionados
RNF08 (Usabilidade)

### RN Relacionadas
RN03
<img width="406" height="312" alt="image" src="https://github.com/user-attachments/assets/00932be4-0e50-4739-9c76-0a58467f5998" />

---

## UC13 — Registrar Presença em Aula 

### Ator Principal
Instrutor

### Objetivo
Confirmar a participação dos alunos presentes na aula.

### Pré-condições
- Aula em andamento ou finalizada.

### Pós-condições
- Lista de presença atualizada no histórico do aluno.

### Fluxo Principal
1.	O instrutor acessa a aula agendada.
2.	O sistema exibe a lista de alunos que reservaram vaga.
3.	O instrutor marca os alunos presentes.
4.	O sistema salva as informações.

### Fluxos Alternativos
- **A1 — Aluno não agendado:**
O instrutor pode adicionar o aluno manualmente se houver vaga.

### RF Relacionados
RF07

### RNF Relacionados
RNF02 (Disponibilidade)

### RN Relacionadas
RN06
 <img width="292" height="451" alt="image" src="https://github.com/user-attachments/assets/a51adc8d-14e8-473f-a44f-266fa90f989a" />

---

## UC14 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Cadastrar métricas corporais do aluno. 

### Pré-condições
- Aluno deve estar ativo e regular (RN05).

### Pós-condições
- Avaliação salva e disponível para consulta.

### Fluxo Principal
1.	O instrutor inicia a avaliação física do aluno.
2.	O sistema verifica o status do aluno (RN05).
3.	O instrutor insere peso, altura, dobras cutâneas e IMC.
4.	O sistema calcula os resultados e salva.

### Fluxos Alternativos
- **A1 — Aluno irregular:**
   O sistema bloqueia a avaliação física.

### RF Relacionados
RF08

### RNF Relacionados
RNF04 (Integridade)

### RN Relacionadas
RN05, RN06
<img width="357" height="367" alt="image" src="https://github.com/user-attachments/assets/81e68027-c2a6-4754-8b87-124bd011a754" />

---

## UC15 — Anexar Arquivos à Avaliação

### Ator Principal
Instrutor

### Objetivo
Adicionar fotos ou laudos externos ao registro de avaliação.

### Pré-condições
- Avaliação física aberta para edição.

### Pós-condições
- Arquivos vinculados ao perfil do aluno.

### Fluxo Principal
1.	O instrutor seleciona a opção "Anexar Arquivos".
2.	O instrutor escolhe as imagens ou PDFs.
3.	O sistema realiza o upload e vincula à avaliação atual.

### Fluxos Alternativos
- **A1 — Arquivo muito grande:**
   O sistema solicita um arquivo menor conforme limite estabelecido.

### RF Relacionados
RF08

### RNF Relacionados
RNF09 (Armazenamento)

### RN Relacionadas
RN06
<img width="350" height="367" alt="image" src="https://github.com/user-attachments/assets/4b18cc6d-5a8f-4a73-84ce-eef99770e37e" />

---

## UC16 — Gerar Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Identificar todos os alunos com pagamentos atrasados.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Lista de inadimplentes exibida/exportada.

### Fluxo Principal
1.	O gerente solicita o relatório de inadimplência.
2.	O sistema filtra os pagamentos vencidos e não pagos.
3.	O sistema exibe nome, valor e dias de atraso.

### Fluxos Alternativos
- **A1 — Filtro por período:**
  O gerente pode restringir a busca por datas específicas.

### RF Relacionados
RF09

### RNF Relacionados
RNF Relacionados

### RN Relacionadas
RN06
<img width="264" height="274" alt="image" src="https://github.com/user-attachments/assets/ac7bd260-6300-4a06-a056-a48f6e2d7042" />

---

## UC17 — Gerar Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Analisar a demanda das modalidades coletivas.

### Pré-condições
- Dados de agendamento e presença existentes.

### Pós-condições
- Relatório com porcentagens de ocupação gerado.

### Fluxo Principal
1.	O gerente acessa "Relatórios de Aulas".
2.	O sistema processa a média de alunos por aula vs. capacidade máxima.
3.	O sistema gera gráficos de desempenho das aulas.

### Fluxos Alternativos
- **A1 — Sem dados:**
   O sistema informa que não há dados suficientes para o período.

### RF Relacionados
RF09

### RNF Relacionados
RNF10 (Geração de relatórios)

### RN Relacionadas
RN06
<img width="251" height="248" alt="image" src="https://github.com/user-attachments/assets/6d669fae-0a54-4453-bb91-be91bd0dc888" />

---

## UC18 — Notificar Vencimento de Mensalidade

### Ator Principal
Sistema

### Objetivo
Alertar o aluno sobre o prazo de pagamento.

### Pré-condições
- Mensalidade próxima do vencimento.

### Pós-condições
- Notificação enviada ao app/e-mail do aluno.

### Fluxo Principal
1.	O sistema identifica parcelas que vencem em 3 dias.
2.	O sistema dispara uma notificação automática (RF10).
3.	O sistema registra o envio no log de comunicações.

### Fluxos Alternativos
- **A1 — Falha no envio:**
  O sistema agenda uma nova tentativa em 4 horas.

### RF Relacionados
RF10

### RNF Relacionados
RNF11 (Confiabilidade de entrega)

### RN Relacionadas
Nenhuma
<img width="220" height="219" alt="image" src="https://github.com/user-attachments/assets/cca5f9fb-7536-4648-8ca7-687f16801410" />

---

## UC19 — Notificar Confirmação de Agendamento

### Ator Principal
Sistema

### Objetivo
Confirmar formalmente que a vaga do aluno foi reservada.

### Pré-condições
- Conclusão bem-sucedida do UC10.

### Pós-condições
- Aluno recebe confirmação instantânea.

### Fluxo Principal
1.	Após a reserva, o sistema gera uma mensagem de confirmação.
2.	O sistema envia notificação push para o aluno.

### Fluxos Alternativos
- **A1 — Aluno desativou notificações:**
  O sistema apenas mantém o registro no portal interno.

### RF Relacionados
RF10

### RNF Relacionados
RNF11 (Confiabilidade)

### RN Relacionadas
Nenhuma
<img width="394" height="312" alt="image" src="https://github.com/user-attachments/assets/73f60972-2ee4-4d35-b546-1802db5017e3" />

---

## UC20 — Notificar Liberação de Avaliação Física

### Ator Principal
Sistema

### Objetivo
Avisar o aluno que seus resultados já podem ser consultados.

### Pré-condições
- Conclusão do UC13 pelo instrutor.

### Pós-condições
- Notificação enviada ao aluno.

### Fluxo Principal
1.	O instrutor finaliza e salva a avaliação.
2.	O sistema identifica a mudança de status da avaliação para "Concluída".
3.	O sistema envia alerta ao aluno (RF10).

### Fluxos Alternativos
- **A1 — Avaliação pendente de revisão:**
  O sistema aguarda a liberação manual pelo instrutor chefe se necessário.

### RF Relacionados
RF10

### RNF Relacionados
RNF11 (Confiabilidade)

### RN Relacionadas
Nenhuma
<img width="244" height="248" alt="image" src="https://github.com/user-attachments/assets/9bfd401b-7bdf-486f-9bca-7ca60ba469e4" />

---

## UC21 — Consultar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Monitorar o fluxo de pessoas e frequência individual.

### Pré-condições
- Registros de catraca existentes (UC08).

### Pós-condições
- Dados de frequência exibidos em tela.

### Fluxo Principal
1.	O gerente busca por um aluno ou data específica.
2.	O sistema recupera todos os registros de entrada e saída.
3.	O sistema exibe o histórico detalhado.

### Fluxos Alternativos
- **A1 — Acesso negado:**
   O sistema destaca em vermelho as tentativas de entrada bloqueadas pela RN01.

### RF Relacionados
RF09

### RNF Relacionados
RNF10 (Relatórios)

### RN Relacionadas
RN01, RN06
<img width="236" height="248" alt="image" src="https://github.com/user-attachments/assets/89ef556d-70c3-49a0-921b-f8c219b34661" />

<img width="463" height="1014" alt="image" src="https://github.com/user-attachments/assets/f871fbc2-04f1-4a4f-b7f0-15b283a09b4f" />


<img width="792" height="813" alt="image" src="https://github.com/user-attachments/assets/f1cabb0b-d662-4c70-8e71-0ba8a06ad49d" />
