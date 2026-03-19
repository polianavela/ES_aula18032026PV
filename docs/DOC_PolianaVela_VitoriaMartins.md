# Documentação de Casos de Uso – FitPass Gym Management

Este documento detalha os 20 casos de uso do sistema FitPass, conforme os requisitos funcionais, não funcionais e regras de negócio estabelecidos.

### UC01 — Cadastrar Aluno

* **Ator Principal:** Recepcionista
* **Objetivo:** Registrar um novo aluno no sistema.
* **Pré-condições:** Recepcionista autenticado.
* **Pós-condições:** Aluno cadastrado e apto a contratar planos.
* **Fluxo Principal:**
1. O recepcionista acessa o menu de cadastro de alunos.
2. O sistema exibe o formulário de dados (nome, CPF, endereço, contato).
3. O recepcionista preenche as informações.
4. O sistema valida os dados e a unicidade do CPF.
5. O sistema confirma a criação do perfil do aluno.


* **Fluxos Alternativos:**
* **A1 — Dados Inválidos:** O sistema sinaliza campos obrigatórios vazios ou CPF inválido e solicita correção.


* **RF Relacionados:** RF01
* **RNF Relacionados:** RNF02, RNF04
* **RN Relacionadas:** RN06
* 
* <img width="523" height="210" alt="image" src="https://github.com/user-attachments/assets/1894951a-45f4-43d7-91d8-dc14a1fe40ab" />


---

### UC02 — Gerenciar Tipos de Planos

* **Ator Principal:** Gerente
* **Objetivo:** Criar, editar ou desativar os planos oferecidos pela academia.
* **Pré-condições:** Gerente autenticado.
* **Pós-condições:** Tabela de planos atualizada para novas matrículas.
* **Fluxo Principal:**
1. O gerente acessa a área de configuração de planos.
2. O gerente define o nome do plano (ex: Musculação), valor, periodicidade e status.
3. O sistema salva as configurações.


* **Fluxos Alternativos:**
* **A1 — Desativar Plano:** O gerente desativa um plano; o sistema impede novas matrículas nele.


* **RF Relacionados:** RF02
* **RNF Relacionados:** RNF04
* **RN Relacionadas:** RN06
* <img width="556" height="211" alt="image" src="https://github.com/user-attachments/assets/a5487681-4580-4565-a2b0-16f26cc611d3" />


---

### UC03 — Registrar Pagamento de Mensalidade

* **Ator Principal:** Recepcionista
* **Objetivo:** Quitar débitos financeiros do aluno na recepção.
* **Pré-condições:** Aluno possuir uma conta/plano ativo.
* **Pós-condições:** Mensalidade baixada e acesso liberado.
* **Fluxo Principal:**
1. O recepcionista localiza o cadastro do aluno.
2. O recepcionista seleciona a parcela em aberto.
3. O recepcionista escolhe a forma de pagamento (Dinheiro, Cartão ou PIX).
4. O sistema processa o pagamento e emite recibo.


* **Fluxos Alternativos:**
* **A1 — Pagamento Parcial:** O sistema bloqueia a operação informando que o valor deve ser integral (RN04).


* **RF Relacionados:** RF03, RF04
* **RNF Relacionados:** RNF02
* **RN Relacionadas:** RN04, RN07
* <img width="649" height="118" alt="image" src="https://github.com/user-attachments/assets/191baed8-b6e8-4dca-a525-0ea55c544a31" />


---

### UC04 — Validar Acesso via RFID (Catraca)

* **Ator Principal:** Sistema de Catraca (API)
* **Objetivo:** Autorizar a entrada física do aluno na academia.
* **Pré-condições:** Aluno possuir tag RFID cadastrada.
* **Pós-condições:** Giro da catraca liberado e registro de log de acesso.
* **Fluxo Principal:**
1. O aluno aproxima a tag do leitor da catraca.
2. O Sistema de Catraca envia o ID via API JSON para o software central.
3. O sistema verifica se a mensalidade está em dia ou com atraso menor que 5 dias.
4. O sistema retorna o comando de liberação para a catraca.


* **Fluxos Alternativos:**
* **A1 — Bloqueio por Inadimplência:** Se o atraso for superior a 5 dias, o acesso é negado (RN01).


* **RF Relacionados:** RF04, RF05
* **RNF Relacionados:** RNF03, RNF06
* **RN Relacionadas:** RN01
<img width="599" height="210" alt="image" src="https://github.com/user-attachments/assets/dbe55093-82fb-48fb-bcb4-c146cceb1548" />

---

### UC05 — Agendar Aula Coletiva

* **Ator Principal:** Aluno
* **Objetivo:** Reservar vaga em aulas de horário marcado.
* **Pré-condições:** Aluno regular e ativo.
* **Pós-condições:** Reserva confirmada no sistema.
* **Fluxo Principal:**
1. O aluno acessa a grade de horários pelo aplicativo mobile.
2. O aluno seleciona a aula desejada e clica em "Agendar".
3. O sistema verifica se há vagas disponíveis (RN02).
4. O sistema confirma a reserva e envia notificação.


* **Fluxos Alternativos:**
* **A1 — Aula Lotada:** O sistema informa que o limite foi atingido e bloqueia a reserva.


* **RF Relacionados:** RF06, RF10
* **RNF Relacionados:** RNF04
* **RN Relacionadas:** RN02
* <img width="611" height="118" alt="image" src="https://github.com/user-attachments/assets/6c660622-6448-45bf-83b1-6e82e9893d76" />


---

### UC06 — Cancelar Reserva de Aula

* **Ator Principal:** Aluno
* **Objetivo:** Desistir de uma vaga previamente reservada.
* **Pré-condições:** Aluno possuir reserva ativa.
* **Pós-condições:** Vaga liberada na grade de aulas.
* **Fluxo Principal:**
1. O aluno acessa seus agendamentos no sistema.
2. O aluno solicita o cancelamento da aula.
3. O sistema valida se o pedido ocorre com mais de 1 hora de antecedência.
4. O sistema confirma o cancelamento.


* **Fluxos Alternativos:**
* **A1 — Fora do Prazo:** O sistema impede o cancelamento se faltar menos de 1 hora (RN03).


* **RF Relacionados:** RF06
* **RNF Relacionados:** RNF04
* **RN Relacionadas:** RN03
* <img width="617" height="118" alt="image" src="https://github.com/user-attachments/assets/aeb5dc2e-1e56-41fb-a0c3-4d335edb97e0" />


---

### UC07 — Registrar Presença em Aula

* **Ator Principal:** Instrutor
* **Objetivo:** Confirmar a presença dos alunos agendados.
* **Pré-condições:** Instrutor autenticado; aula em horário de realização.
* **Pós-condições:** Lista de frequência atualizada.
* **Fluxo Principal:**
1. O instrutor abre a lista de alunos agendados para a aula atual.
2. O instrutor marca o check-in dos alunos que compareceram.
3. O sistema salva a lista de presença para fins de relatório.


* **RF Relacionados:** RF07
* **RN Relacionadas:** RN06
* <img width="344" height="111" alt="image" src="https://github.com/user-attachments/assets/0501fbe3-4290-402d-a895-2dc4bbaefe6f" />


---

### UC08 — Realizar Avaliação Física

* **Ator Principal:** Instrutor
* **Objetivo:** Cadastrar medidas e dados biométricos do aluno.
* **Pré-condições:** Aluno regular e ativo (RN05).
* **Pós-condições:** Dados da avaliação salvos no perfil do aluno.
* **Fluxo Principal:**
1. O instrutor inicia o módulo de avaliação física.
2. O instrutor insere peso, altura, IMC e percentual de gordura.
3. O sistema valida se o aluno está apto para a avaliação.
4. O sistema salva os dados e gera o resultado.


* **Fluxos Alternativos:**
* **A1 — Aluno Inativo/Irregular:** O sistema impede a gravação conforme RN05.


* **RF Relacionados:** RF08
* **RNF Relacionados:** RNF02
* **RN Relacionadas:** RN05, RN06
* <img width="679" height="118" alt="image" src="https://github.com/user-attachments/assets/f18ecc46-eb3d-4696-922a-b98c36a44b6c" />


---

### UC09 — Emitir Relatório de Inadimplência

* **Ator Principal:** Gerente
* **Objetivo:** Listar alunos com pagamentos em atraso.
* **Pré-condições:** Gerente autenticado.
* **Pós-condições:** Relatório consolidado gerado na tela.
* **Fluxo Principal:**
1. O gerente seleciona o relatório de inadimplência no painel.
2. O sistema filtra os alunos com mensalidades vencidas.
3. O sistema exibe nome, telefone e dias de atraso.


* **RF Relacionados:** RF09
* **RN Relacionadas:** RN06
* <img width="421" height="127" alt="image" src="https://github.com/user-attachments/assets/07e6c8f2-576b-4335-a4ae-62b440994808" />


---

### UC10 — Enviar Notificação de Vencimento

* **Ator Principal:** Sistema
* **Objetivo:** Alertar o aluno sobre o prazo de pagamento da mensalidade.
* **Pré-condições:** Data de vencimento se aproximando.
* **Pós-condições:** Notificação enviada ao dispositivo do aluno.
* **Fluxo Principal:**
1. O sistema verifica as faturas que vencem em 3 dias.
2. O sistema dispara automaticamente uma notificação push.


* **RF Relacionados:** RF10
* **RNF Relacionados:** RNF05
* <img width="460" height="127" alt="image" src="https://github.com/user-attachments/assets/f4f0b49d-4a31-4f17-865a-5974ab58f055" />


---

### UC11 — Editar Cadastro de Aluno

* **Ator Principal:** Recepcionista
* **Objetivo:** Atualizar informações de endereço ou contato do aluno.
* **Fluxo Principal:**
1. O recepcionista busca o aluno pelo CPF.
2. O sistema exibe os dados atuais.
3. O recepcionista altera os campos e salva.


* **RF Relacionados:** RF01
* <img width="414" height="117" alt="image" src="https://github.com/user-attachments/assets/c77ce8ef-e056-4459-bd38-b722fe2f13b8" />


---

### UC12 — Gerar Boleto para Pagamento Online

* **Ator Principal:** Aluno
* **Objetivo:** Emitir cobrança para pagamento via internet.
* **Fluxo Principal:**
1. O aluno acessa o módulo financeiro no aplicativo.
2. O aluno seleciona a mensalidade vigente.
3. O sistema gera o boleto ou chave PIX.


* **RF Relacionados:** RF03
* <img width="331" height="111" alt="image" src="https://github.com/user-attachments/assets/7ac1d36e-887b-4541-834b-76f5d4a51d54" />


---

### UC13 — Consultar Histórico de Acessos

* **Ator Principal:** Gerente
* **Objetivo:** Monitorar o fluxo de alunos na unidade.
* **Fluxo Principal:**
1. O gerente filtra o relatório por data e horário.
2. O sistema lista os logs gerados pela catraca.


* **RF Relacionados:** RF09
* <img width="412" height="125" alt="image" src="https://github.com/user-attachments/assets/dfb46191-8ed5-4e33-9651-45151a258c45" />


---

### UC14 — Visualizar Resultados de Avaliação Física

* **Ator Principal:** Aluno
* **Objetivo:** Acompanhar o progresso físico através do aplicativo.
* **Fluxo Principal:**
1. O aluno acessa a aba "Avaliações".
2. O sistema exibe os dados cadastrados pelo instrutor e arquivos anexos.


* **RF Relacionados:** RF08, RF10
* <img width="368" height="119" alt="image" src="https://github.com/user-attachments/assets/344bf883-4ffb-4505-b51f-8d928e77c600" />


---

### UC15 — Emitir Relatório de Ocupação de Aulas

* **Ator Principal:** Gerente
* **Objetivo:** Analisar a lotação das turmas.
* **Fluxo Principal:**
1. O gerente solicita o relatório de ocupação.
2. O sistema compara as vagas totais (RN02) com os agendamentos realizados.


* **RF Relacionados:** RF09
* <img width="421" height="127" alt="image" src="https://github.com/user-attachments/assets/e7d071fb-9a1e-49e1-b9a1-4ecd4c289c4e" />


---

### UC16 — Anexar Exames à Avaliação

* **Ator Principal:** Instrutor
* **Objetivo:** Salvar arquivos externos no prontuário do aluno.
* **Fluxo Principal:**
1. Durante a avaliação física, o instrutor seleciona "Anexar Arquivo".
2. O sistema faz o upload e vincula o arquivo à avaliação.


* **RF Relacionados:** RF08
* **RNF Relacionados:** RNF02
* <img width="695" height="121" alt="image" src="https://github.com/user-attachments/assets/b33ff8f5-c776-4ba0-bd01-fd95dcf3e6b7" />


---

### UC17 — Notificar Confirmação de Agendamento

* **Ator Principal:** Sistema
* **Objetivo:** Confirmar a vaga do aluno via push/e-mail.
* **Fluxo Principal:**
1. Após o sucesso do UC05, o sistema envia mensagem automática de confirmação.


* **RF Relacionados:** RF10
* <img width="695" height="121" alt="image" src="https://github.com/user-attachments/assets/ec00ab58-d7f2-4a19-b4b1-50f725dad9d5" />


---

### UC18 — Consultar Lista de Alunos Ativos

* **Ator Principal:** Gerente
* **Objetivo:** Visualizar o total de matrículas vigentes.
* **Fluxo Principal:**
1. O gerente solicita o relatório de alunos ativos.
2. O sistema extrai a lista de alunos com contratos não expirados.


* **RF Relacionados:** RF09
* <img width="369" height="117" alt="image" src="https://github.com/user-attachments/assets/dbe68c57-e711-4f8b-9010-cd7a95114e69" />


---

### UC19 — Matricular Aluno em Plano

* **Ator Principal:** Recepcionista
* **Objetivo:** Vincular um aluno a um plano de pagamento específico.
* **Fluxo Principal:**
1. O recepcionista seleciona o aluno e o plano escolhido.
2. O sistema gera as faturas recorrentes e libera o acesso.


* **RF Relacionados:** RF01, RF02
* <img width="420" height="119" alt="image" src="https://github.com/user-attachments/assets/a3bc1c3b-8aba-4ab9-8482-008f16025b1c" />


---

### UC20 — Atualização Automática de Regularidade

* **Ator Principal:** Sistema
* **Objetivo:** Sincronizar o status de acesso imediatamente após o pagamento.
* **Fluxo Principal:**
1. O sistema detecta o pagamento via PIX/Cartão.
2. O sistema altera o status do aluno para "Regular" instantaneamente (RN07).


* **RF Relacionados:** RF04
* **RN Relacionadas:** RN07
* <img width="502" height="135" alt="image" src="https://github.com/user-attachments/assets/62814a40-91da-45fd-9867-50d355a33a80" />

