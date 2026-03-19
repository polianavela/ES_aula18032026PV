1. Bloco: Ator Recepcionista
Referente ao diagrama Diagrama_Recepcionista

UC01 — Cadastrar Aluno

Objetivo: Registrar um novo aluno no sistema.

Fluxo Principal: O recepcionista acessa o menu, preenche o formulário (nome, CPF, etc.), o sistema valida o CPF e confirma a criação do perfil.

Fluxos Alternativos: A1 — Dados Inválidos: Sistema sinaliza erro em campos vazios ou CPF inválido.

UC03 — Registrar Pagamento de Mensalidade

Objetivo: Quitar débitos financeiros do aluno na recepção.

Fluxo Principal: Localiza o aluno, seleciona a parcela, escolhe a forma de pagamento (Dinheiro, Cartão ou PIX) e emite o recibo.

Fluxos Alternativos: A1 — Pagamento Parcial: Sistema bloqueia a operação (exige valor integral).

UC11 — Editar Cadastro de Aluno

Objetivo: Atualizar informações de endereço ou contato do aluno.

Fluxo Principal: Busca o aluno pelo CPF, exibe os dados e o recepcionista salva as alterações.

UC19 — Matricular Aluno em Plano

Objetivo: Vincular um aluno a um plano de pagamento específico.

Fluxo Principal: Seleciona o aluno e o plano, o sistema gera as faturas recorrentes e libera o acesso.
<img width="744" height="366" alt="image" src="https://github.com/user-attachments/assets/a606cc82-d973-4eab-b564-d26ae114c3ac" />


2. Bloco: Ator Gerente
Referente ao diagrama Diagrama_Gerente

UC02 — Gerenciar Tipos de Planos

Objetivo: Criar, editar ou desativar os planos oferecidos.

Fluxo Principal: Define nome, valor e periodicidade. Sistema salva as configurações.

Fluxos Alternativos: A1 — Desativar Plano: Impede novas matrículas no plano desativado.

UC09 — Emitir Relatório de Inadimplência

Objetivo: Listar alunos com pagamentos em atraso.

Fluxo Principal: Filtra alunos com mensalidades vencidas e exibe nome, contato e dias de atraso.

UC13 — Consultar Histórico de Acessos

Objetivo: Monitorar o fluxo de alunos na unidade através dos logs da catraca.

UC15 — Emitir Relatório de Ocupação de Aulas

Objetivo: Analisar a lotação das turmas comparando vagas totais com agendamentos.

UC18 — Consultar Lista de Alunos Ativos

Objetivo: Visualizar o total de matrículas vigentes (contratos não expirados).
<img width="725" height="510" alt="image" src="https://github.com/user-attachments/assets/842c0014-7be8-424c-b7c4-c3fac930e8b6" />


3. Bloco: Ator Aluno
Referente ao diagrama Diagrama_Aluno

UC05 — Agendar Aula Coletiva

Objetivo: Reservar vaga em aulas pelo aplicativo mobile.

Fluxo Principal: Seleciona a aula, sistema verifica vagas e confirma a reserva com notificação.

Fluxos Alternativos: A1 — Aula Lotada: Sistema bloqueia a reserva informando limite atingido.

UC06 — Cancelar Reserva de Aula

Objetivo: Desistir de uma vaga reservada com antecedência.

Fluxo Principal: Solicita cancelamento; sistema valida se falta mais de 1 hora para a aula.

Fluxos Alternativos: A1 — Fora do Prazo: Sistema impede o cancelamento (menos de 1h).

UC12 — Gerar Boleto para Pagamento Online

Objetivo: Emitir cobrança (Boleto ou PIX) diretamente pelo aplicativo.

UC14 — Visualizar Resultados de Avaliação Física

Objetivo: Aluno acompanha seu progresso e arquivos anexos pelo aplicativo.
<img width="744" height="396" alt="image" src="https://github.com/user-attachments/assets/aa4fd6df-3963-4642-805a-0d65fb4630c1" />


4. Bloco: Ator Instrutor
Referente ao diagrama Diagrama_Instrutor

UC07 — Registrar Presença em Aula

Objetivo: Confirmar o check-in dos alunos agendados que compareceram à aula.

UC08 — Realizar Avaliação Física

Objetivo: Cadastrar medidas (peso, IMC, etc.) do aluno.

Fluxo Principal: Insere os dados; sistema valida se o aluno está regular para salvar o resultado.

Fluxos Alternativos: A1 — Aluno Inativo: Sistema impede a gravação dos dados.

UC16 — Anexar Exames à Avaliação

Objetivo: Upload de arquivos externos para o prontuário do aluno durante a avaliação.
<img width="744" height="179" alt="image" src="https://github.com/user-attachments/assets/201f6da1-940c-4be9-b7de-7af42c4c30dc" />


5. Bloco: Ator Sistema (Automático / Catraca)
Referente ao diagrama Diagrama_Sistema

UC04 — Validar Acesso via RFID (Catraca)

Objetivo: Autorizar a entrada física do aluno.

Fluxo Principal: Aluno aproxima a tag; sistema verifica mensalidade (atraso < 5 dias) e libera giro.

Fluxos Alternativos: A1 — Bloqueio por Inadimplência: Acesso negado se o atraso for > 5 dias.

UC10 — Enviar Notificação de Vencimento

Objetivo: Disparo automático de push 3 dias antes do vencimento da fatura.

UC17 — Notificar Confirmação de Agendamento

Objetivo: Envio automático de confirmação após o aluno reservar uma aula (UC05).

UC20 — Atualização Automática de Regularidade

Objetivo: Sincronizar o status para "Regular" instantaneamente após a detecção do pagamento.
<img width="744" height="350" alt="image" src="https://github.com/user-attachments/assets/cccc6afb-40af-4559-9945-c34e4637066c" />
