UC01 — Realizar Matrícula
Ator Principal
Aluno; Recepcionista

Objetivo
Registrar um novo aluno no sistema, criando suas credenciais de acesso e vínculo com a academia.

Pré-condições
Recepcionista autenticado no sistema.
CPF do aluno não cadastrado anteriormente.

Pós-condições
Aluno cadastrado com login e credencial biométrica/RFID ativa.
Aluno apto a contratar planos.

Fluxo Principal
O aluno informa nome, CPF, data de nascimento, endereço, e-mail e senha.
O recepcionista valida os dados inseridos.
O sistema verifica a unicidade do CPF.
O sistema cria o perfil do aluno e gera credencial de acesso.
O sistema confirma o cadastro com sucesso.

Fluxos Alternativos
A1 — CPF já cadastrado:

O sistema exibe mensagem de erro informando duplicidade e bloqueia o cadastro.
A2 — Dados obrigatórios ausentes:

O sistema sinaliza os campos inválidos e solicita correção antes de prosseguir.

RF Relacionados
RF01

RNF Relacionados
RNF01, RNF02

RN Relacionadas
RN06

<img width="488" height="369" alt="image" src="https://github.com/user-attachments/assets/1fb77a1e-0ca8-4427-b441-381d2e99ecad" />


UC02 — Escolher Plano de Mensalidade
Ator Principal
Aluno; Recepcionista

Objetivo
Definir o plano contratado pelo aluno, associando-o à cobrança recorrente.

Pré-condições
Aluno possuir cadastro ativo no sistema.
Planos disponíveis configurados pelo gerente.

Pós-condições
Plano vinculado ao aluno com faturas geradas.
Aluno habilitado a utilizar os serviços do plano escolhido.

Fluxo Principal
O recepcionista acessa o perfil do aluno no sistema.
O sistema exibe os planos ativos disponíveis.
O aluno escolhe o plano desejado.
O sistema registra o vínculo e gera as faturas recorrentes.

Fluxos Alternativos
A1 — Plano indisponível:

O sistema informa que o plano está desativado e exibe apenas planos ativos.
A2 — Aluno já vinculado a outro plano:

O sistema solicita encerramento do plano anterior antes de prosseguir.

RF Relacionados
RF02, RF03

RNF Relacionados
RNF01, RNF02

RN Relacionadas
RN01, RN04, RN07

<img width="467" height="663" alt="image" src="https://github.com/user-attachments/assets/99d85f89-3149-4c7b-84dd-bfc1924eed66" />


UC03 — Agendar Aula Coletiva
Ator Principal
Aluno; Instrutor

Objetivo
Reservar vaga em aula coletiva de horário marcado.

Pré-condições
Aluno regular, com pagamento em dia.
Vagas disponíveis na aula desejada.

Pós-condições
Reserva confirmada; aluno incluído na lista de presença esperada.

Fluxo Principal
O aluno acessa a grade de horários pelo aplicativo.
O aluno seleciona a aula desejada e clica em "Agendar".
O instrutor valida se há disponibilidade de vagas.
O sistema registra a reserva e envia notificação de confirmação ao aluno.

Fluxos Alternativos
A1 — Aula com vagas esgotadas:

O sistema informa que o limite de vagas foi atingido (RN02) e bloqueia o agendamento.
A2 — Aluno inadimplente:

O sistema impede o agendamento até regularização do pagamento (RN01).

RF Relacionados
RF06

RNF Relacionados
RNF01, RNF04

RN Relacionadas
RN01, RN02, RN05

<img width="586" height="421" alt="image" src="https://github.com/user-attachments/assets/04876d93-6514-4936-9b50-ff0522c0e6c6" />


UC04 — Agendar Avaliação Física
Ator Principal
Aluno; Instrutor

Objetivo
Agendar uma sessão de avaliação física com instrutor disponível.

Pré-condições
Aluno regular com pagamento em dia.
Instrutor com horários disponíveis.

Pós-condições
Agendamento de avaliação criado para o instrutor e aluno; notificação enviada.

Fluxo Principal
O aluno acessa o módulo de agendamentos no aplicativo.
O aluno escolhe um horário e um instrutor disponível.
O instrutor valida o agendamento no sistema.
O sistema registra a avaliação e notifica o aluno.

Fluxos Alternativos
A1 — Horário não disponível:

O sistema exibe os horários livres disponíveis e solicita nova escolha.
A2 — Instrutor não disponível:

O sistema lista os instrutores disponíveis no horário e solicita nova seleção.

RF Relacionados
RF06, RF08

RNF Relacionados
RNF01, RNF03, RNF04

RN Relacionadas
RN02, RN03, RN05

<img width="288" height="855" alt="image" src="https://github.com/user-attachments/assets/349c6ab3-a8bb-4554-bcf5-9f3f65ae0754" />


UC05 — Realizar Cadastro Facial
Ator Principal
Aluno; Recepcionista

Objetivo
Registrar a biometria facial do usuário para identificação no sistema de acesso por catraca.

Pré-condições
Usuário possuir cadastro ativo no sistema.
Pagamento em dia (para aluno).

Pós-condições
Sistema passa a identificar o usuário via reconhecimento facial na catraca.

Fluxo Principal
O recepcionista inicia o módulo de cadastro facial no sistema.
O usuário posiciona o rosto diante da câmera indicada.
O sistema captura e processa os dados biométricos.
O sistema vincula a biometria ao perfil do usuário.
O sistema confirma o cadastro facial com sucesso.

Fluxos Alternativos
A1 — Falha no reconhecimento facial:

O sistema solicita nova captura, informando que não foi possível processar a imagem.
A2 — Biometria já cadastrada:

O sistema solicita confirmação para sobrescrever o registro anterior.

RF Relacionados
RF05

RNF Relacionados
RNF01, RNF03, RNF06

RN Relacionadas
RN06

<img width="488" height="657" alt="image" src="https://github.com/user-attachments/assets/312212c8-c194-443d-87a0-3d82ce87499d" />


UC06 — Realizar Login no Sistema
Ator Principal
Aluno; Recepcionista; Instrutor; Gerente

Objetivo
Autenticar o usuário no sistema FitPass para acesso às funcionalidades de seu perfil.

Pré-condições
Usuário possuir cadastro ativo no sistema.

Pós-condições
Usuário autenticado e com acesso às funcionalidades correspondentes ao seu perfil.

Fluxo Principal
O usuário acessa a tela de login do sistema ou aplicativo.
O usuário informa e-mail e senha.
O sistema valida as credenciais informadas.
O sistema redireciona o usuário ao painel correspondente ao seu perfil.

Fluxos Alternativos
A1 — Credenciais inválidas:

O sistema exibe mensagem de erro e solicita nova tentativa.
A2 — Conta inativa/bloqueada:

O sistema informa que a conta está suspensa e orienta o usuário a contatar a recepção.

RF Relacionados
RF01

RNF Relacionados
RNF01, RNF02

RN Relacionadas
RN06

<img width="488" height="310" alt="image" src="https://github.com/user-attachments/assets/ffc6d0b4-0651-4e7d-b30a-417386b087b2" />


UC07 — Definir Método de Pagamento
Ator Principal
Aluno

Objetivo
Selecionar a forma de pagamento preferencial para quitação das mensalidades.

Pré-condições
Aluno autenticado no sistema.
Aluno vinculado a um plano ativo.

Pós-condições
Método de pagamento registrado; próximas faturas geradas conforme a escolha.

Fluxo Principal
O aluno acessa o módulo financeiro no aplicativo.
O aluno seleciona o método desejado: Cartão de Crédito, PIX ou Boleto.
O aluno informa os dados necessários para o método escolhido.
O sistema registra a preferência e aplica às faturas futuras.

Fluxos Alternativos
A1 — Dados de pagamento inválidos:

O sistema sinaliza o erro e solicita revisão das informações inseridas.

RF Relacionados
RF03

RNF Relacionados
RNF01, RNF02

RN Relacionadas
RN04, RN07

<img width="449" height="495" alt="image" src="https://github.com/user-attachments/assets/3ad18aa0-1a8e-459b-a24f-c68b0f9ddf0e" />


UC08 — Registrar Pagamento de Mensalidade
Ator Principal
Recepcionista

Objetivo
Quitar débitos financeiros do aluno presencialmente na recepção da academia.

Pré-condições
Recepcionista autenticado no sistema.
Aluno possuir fatura em aberto.

Pós-condições
Mensalidade quitada; status do aluno atualizado para "Regular"; recibo emitido.

Fluxo Principal
O recepcionista localiza o cadastro do aluno pelo CPF.
O sistema exibe as faturas em aberto do aluno.
O recepcionista seleciona a parcela e informa a forma de pagamento.
O sistema processa o pagamento e emite o recibo.
O sistema atualiza o status do aluno para "Regular" imediatamente (RN07).

Fluxos Alternativos
A1 — Valor insuficiente:

O sistema bloqueia a operação informando que pagamentos parciais não são aceitos (RN04).

RF Relacionados
RF03, RF04

RNF Relacionados
RNF02

RN Relacionadas
RN04, RN07

<img width="434" height="565" alt="image" src="https://github.com/user-attachments/assets/ad1d86da-dd63-4c64-882f-7b0ca3e07e16" />


UC09 — Matricular Aluno em Plano
Ator Principal
Recepcionista

Objetivo
Vincular formalmente um aluno a um plano de pagamento ativo, gerando as cobranças recorrentes.

Pré-condições
Recepcionista autenticado no sistema.
Aluno e plano previamente cadastrados.

Pós-condições
Aluno vinculado ao plano; faturas geradas; acesso liberado ao sistema.

Fluxo Principal
O recepcionista seleciona o aluno e o plano desejado.
O sistema exibe o resumo do plano (valor, periodicidade e serviços inclusos).
O recepcionista confirma a matrícula.
O sistema gera as faturas recorrentes e libera o acesso do aluno.

Fluxos Alternativos
A1 — Plano desativado:

O sistema impede a seleção e exibe somente os planos ativos disponíveis.

RF Relacionados
RF01, RF02

RNF Relacionados
RNF02

RN Relacionadas
RN06

<img width="488" height="450" alt="image" src="https://github.com/user-attachments/assets/8e256419-6976-4579-826a-12d6d01382bb" />


UC10 — Realizar Suporte ao Usuário
Ator Principal
Recepcionista

Objetivo
Auxiliar alunos com dúvidas, problemas ou solicitações relacionadas ao sistema ou à academia.

Pré-condições
Recepcionista autenticado no sistema.

Pós-condições
Solicitação do aluno registrada ou resolvida no sistema.

Fluxo Principal
O aluno apresenta a solicitação ao recepcionista presencialmente.
O recepcionista localiza o cadastro do aluno pelo CPF.
O recepcionista registra ou resolve a ocorrência no sistema.
O sistema confirma o registro da ocorrência e notifica o aluno, se aplicável.

Fluxos Alternativos
A1 — Aluno não localizado:

O sistema informa que o CPF informado não está cadastrado e solicita verificação dos dados.

RF Relacionados
RF01

RNF Relacionados
RNF02, RNF04

RN Relacionadas
RN06

<img width="488" height="569" alt="image" src="https://github.com/user-attachments/assets/7f52d487-1158-470a-a422-b1497231deee" />


UC11 — Realizar Avaliação Física
Ator Principal
Instrutor

Objetivo
Cadastrar medidas e dados biométricos do aluno durante a sessão de avaliação agendada.

Pré-condições
Instrutor autenticado no sistema.
Aluno regular e com situação ativa no sistema (RN05).

Pós-condições
Dados biométricos salvos no perfil do aluno; histórico de avaliação atualizado.

Fluxo Principal
O instrutor inicia o módulo de avaliação física no sistema.
O instrutor insere peso, altura, IMC, percentual de gordura e observações clínicas.
O sistema valida se o aluno está em situação regular (RN05).
O sistema salva os dados e gera o resultado de evolução do aluno.

Fluxos Alternativos
A1 — Aluno irregular/inadimplente:

O sistema impede o registro da avaliação conforme RN05.
A2 — Dados biométricos incompletos:

O sistema sinaliza os campos obrigatórios pendentes antes de salvar.

RF Relacionados
RF08

RNF Relacionados
RNF02

RN Relacionadas
RN05, RN06

<img width="488" height="411" alt="image" src="https://github.com/user-attachments/assets/c64bcb10-b522-49ba-b95d-6f94427a03d9" />


UC12 — Registrar Presença dos Alunos
Ator Principal
Instrutor

Objetivo
Confirmar a presença dos alunos na aula coletiva realizada.

Pré-condições
Instrutor autenticado no sistema.
Aula em andamento ou recém-concluída.

Pós-condições
Lista de frequência atualizada no sistema para fins de relatório.

Fluxo Principal
O instrutor acessa a lista de alunos agendados para a aula atual.
O instrutor marca o check-in dos alunos presentes.
O sistema salva a lista de frequência com data e horário.

Fluxos Alternativos
A1 — Aluno presente não encontrado na lista:

O sistema permite registro manual de presença com justificativa do instrutor.

RF Relacionados
RF07

RNF Relacionados
RNF02

RN Relacionadas
RN06

<img width="325" height="500" alt="image" src="https://github.com/user-attachments/assets/539da357-e081-4520-9b99-f4327e605421" />


UC13 — Cancelar Agendamento de Aula
Ator Principal
Aluno

Objetivo
Desistir de uma vaga previamente reservada em aula coletiva dentro do prazo permitido.

Pré-condições
Aluno possuir reserva ativa no sistema.
Solicitação realizada com mais de 1 hora de antecedência (RN03).

Pós-condições
Vaga liberada na grade; reserva removida do histórico do aluno.

Fluxo Principal
O aluno acessa seus agendamentos no aplicativo.
O aluno seleciona a aula desejada e solicita o cancelamento.
O sistema valida se a solicitação ocorre com mais de 1 hora de antecedência.
O sistema confirma o cancelamento e libera a vaga para novos agendamentos.

Fluxos Alternativos
A1 — Cancelamento fora do prazo:

O sistema bloqueia o cancelamento quando faltam menos de 1 hora para a aula (RN03).

RF Relacionados
RF06

RNF Relacionados
RNF04

RN Relacionadas
RN03

<img width="466" height="429" alt="image" src="https://github.com/user-attachments/assets/17bde012-f516-4ad2-8218-6de3bbbcc4b7" />


UC14 — Visualizar Resultados de Avaliação Física
Ator Principal
Aluno

Objetivo
Consultar os dados biométricos e o histórico de evolução física registrado pelo instrutor.

Pré-condições
Aluno autenticado no sistema.
Ao menos uma avaliação física registrada no perfil do aluno.

Pós-condições
Dados de avaliação exibidos na tela para consulta do aluno.

Fluxo Principal
O aluno acessa a aba "Avaliações" no aplicativo.
O sistema exibe o histórico de avaliações com datas e resultados.
O aluno seleciona uma avaliação específica para ver os detalhes completos.

Fluxos Alternativos
A1 — Nenhuma avaliação registrada:

O sistema exibe mensagem informando ausência de registros e orienta o aluno a agendar uma avaliação.

RF Relacionados
RF08

RNF Relacionados
RNF04

RN Relacionadas
RN05

<img width="488" height="420" alt="image" src="https://github.com/user-attachments/assets/d6e23209-a991-4a2b-b507-e27aeb890f97" />


UC15 — Gerar Relatório de Inadimplência
Ator Principal
Gerente

Objetivo
Listar e analisar os alunos com pagamentos em atraso para tomada de decisão gerencial.

Pré-condições
Gerente autenticado no sistema.

Pós-condições
Relatório consolidado de inadimplentes exibido e disponível para exportação.

Fluxo Principal
O gerente acessa o painel gerencial e seleciona o relatório de inadimplência.
O gerente define o período de análise desejado.
O sistema filtra os alunos com mensalidades vencidas no período.
O sistema exibe nome, contato e quantidade de dias em atraso de cada aluno.

Fluxos Alternativos
A1 — Nenhum inadimplente no período:

O sistema exibe mensagem informando ausência de inadimplências no período selecionado.

RF Relacionados
RF09

RNF Relacionados
RNF02, RNF04

RN Relacionadas
RN01, RN06

<img width="476" height="441" alt="image" src="https://github.com/user-attachments/assets/1ad800e1-9d26-4d81-a8c8-f7ec1d4b1aeb" />


UC16 — Gerar Relatório de Ocupação de Aulas
Ator Principal
Gerente

Objetivo
Analisar a taxa de ocupação das aulas coletivas por período e modalidade.

Pré-condições
Gerente autenticado no sistema.

Pós-condições
Relatório com dados de vagas e percentual de ocupação exibido na tela.

Fluxo Principal
O gerente seleciona o relatório de ocupação no painel gerencial.
O gerente define o período e a modalidade de aula desejada.
O sistema compara as vagas totais com os agendamentos realizados (RN02).
O sistema exibe o percentual de ocupação por turma e por período.

Fluxos Alternativos
A1 — Nenhuma aula registrada no período:

O sistema informa a ausência de registros para os filtros selecionados.

RF Relacionados
RF09

RNF Relacionados
RNF04

RN Relacionadas
RN02

<img width="488" height="398" alt="image" src="https://github.com/user-attachments/assets/c2c8cbd4-11ae-4e08-a286-3bf3b612c859" />


UC17 — Verificar Pagamentos em Atraso
Ator Principal
Gerente

Objetivo
Monitorar o status financeiro dos alunos e identificar casos críticos de inadimplência para ação imediata.

Pré-condições
Gerente autenticado no sistema.

Pós-condições
Lista de alunos com atrasos críticos exibida; gerente apto a tomar ações corretivas.

Fluxo Principal
O gerente acessa a seção de monitoramento financeiro no painel.
O sistema lista os alunos com atrasos superiores a 5 dias (RN01).
O gerente seleciona um aluno para visualizar o histórico de pagamentos.

Fluxos Alternativos
A1 — Nenhum atraso crítico identificado:

O sistema exibe mensagem informando que não há alunos com atraso superior a 5 dias.

RF Relacionados
RF04, RF09

RNF Relacionados
RNF04

RN Relacionadas
RN01

<img width="459" height="441" alt="image" src="https://github.com/user-attachments/assets/08e9d9bb-b286-4e18-a54c-171add630a45" />


UC18 — Reconhecer Usuário via Biometria
Ator Principal
Sistema de Catraca

Objetivo
Identificar o usuário que está tentando acessar a academia por meio de reconhecimento facial ou RFID.

Pré-condições
Usuário possuir biometria facial ou tag RFID cadastrada no sistema.

Pós-condições
Identidade do usuário confirmada; sistema aguarda verificação de regularidade financeira.

Fluxo Principal
O usuário se posiciona diante do leitor da catraca.
O Sistema de Catraca captura a biometria facial ou lê a tag RFID via API.
O sistema consulta a base de dados e retorna a identidade do usuário.
O sistema identifica o tipo de cadastro do usuário (aluno, instrutor, gerente).

Fluxos Alternativos
A1 — Biometria/RFID não reconhecido:

O sistema nega o acesso e registra log de tentativa não identificada.

RF Relacionados
RF05

RNF Relacionados
RNF03, RNF06

RN Relacionadas
RN06

<img width="451" height="484" alt="image" src="https://github.com/user-attachments/assets/13ad4ffd-f3b1-468a-b92e-f3363829f588" />


UC19 — Liberar Acesso via Catraca
Ator Principal
Sistema de Catraca

Objetivo
Autorizar a entrada física do aluno após verificação positiva de identidade e regularidade financeira.

Pré-condições
Usuário identificado com sucesso pelo sistema (UC18).
Mensalidade em dia ou com atraso inferior a 5 dias (RN01).

Pós-condições
Catraca liberada; log de acesso registrado com horário e identidade do usuário.

Fluxo Principal
O sistema verifica a regularidade financeira do aluno após o reconhecimento.
O sistema confirma que o atraso é inferior a 5 dias (RN01).
O sistema retorna o comando de liberação para a catraca via API.
O sistema registra o log de acesso com data, horário e identidade.

Fluxos Alternativos
A1 — Falha na comunicação com a catraca:

O sistema registra o erro e aciona alerta para a recepção.

RF Relacionados
RF04, RF05

RNF Relacionados
RNF03, RNF06

RN Relacionadas
RN01

<img width="488" height="382" alt="image" src="https://github.com/user-attachments/assets/566001c0-40c1-4742-990c-b9a2f374ca0e" />


UC20 — Vetar Acesso por Inadimplência
Ator Principal
Sistema de Catraca

Objetivo
Bloquear a entrada de alunos com pagamento em atraso superior ao limite definido pelas regras de negócio.

Pré-condições
Usuário identificado pelo sistema de catraca (UC18).
Mensalidade com atraso superior a 5 dias (RN01).

Pós-condições
Acesso negado; log de bloqueio registrado; aluno orientado a regularizar situação na recepção.

Fluxo Principal
O sistema verifica a data de vencimento da mensalidade do aluno identificado.
O sistema constata atraso superior a 5 dias.
O sistema envia comando de bloqueio para a catraca via API.
A catraca exibe mensagem orientando o aluno a procurar a recepção.
O sistema registra o log do bloqueio com data, horário e motivo.

Fluxos Alternativos
A1 — Aluno contesta o bloqueio:

A recepção consulta o sistema; caso o pagamento tenha sido efetuado recentemente, o status é atualizado manualmente e o acesso é liberado.

RF Relacionados
RF04, RF05

RNF Relacionados
RNF03, RNF06

RN Relacionadas
RN01

<img width="445" height="808" alt="image" src="https://github.com/user-attachments/assets/1a982352-6387-4658-a4c6-cc4a465039f6" />
