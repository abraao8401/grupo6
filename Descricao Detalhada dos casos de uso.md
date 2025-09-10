# Casos de Uso - Sistema de Estacionamento

## 1. Caso de Uso: Registrar Check-in do Veículo

**Ator Principal:** Atendente

**Descrição:** Permite registrar a entrada de um veículo no estacionamento, atribuindo uma vaga disponível.

**Fluxo Principal:**
1. O atendente acessa a aplicação e seleciona a opção "Fazer Check-in".
2. O sistema exibe o mapa do estacionamento com as vagas disponíveis/ocupadas.
3. O atendente informa a placa do veículo.
4. O sistema registra automaticamente o horário de entrada.
5. O atendente seleciona a vaga disponível para o veículo.
6. O sistema registra a vaga ocupada e conclui o check-in.

**Regras de Negócio:**
* O horário de entrada é sempre o horário da finalização do processo.
* A placa do veículo é o identificador do cliente no estacionamento.

**Fluxos de Exceção:**
* **FA1:** O atendente tenta registrar um veículo, mas não há vagas disponíveis. → O sistema exibe mensagem de "Estacionamento Lotado" e não permite concluir o check-in.
* **FA2:** O atendente digita a placa incorretamente ou deixa em branco. → O sistema solicita que a placa seja corrigida antes de concluir.
* **FA3:** O atendente seleciona uma vaga, mas o motorista estaciona em outra diferente. → O atendente deve atualizar manualmente no sistema a vaga correta antes de finalizar o check-in.

---

## 2. Caso de Uso: Registrar Check-out do Veículo

**Ator Principal:** Atendente

**Descrição:** Permite registrar a saída do veículo, calcular o valor devido e liberar a vaga.

**Fluxo Principal:**
1. O atendente acessa a seção de check-out.
2. O sistema calcula o tempo de permanência (em minutos).
3. O sistema calcula o valor = tarifa por minuto × tempo total.
4. O cliente realiza o pagamento no caixa.
5. O atendente confirma o pagamento no sistema.
6. O sistema libera a vaga ocupada.

**Regra de Negócio:**
* O cálculo do valor deve ser feito automaticamente.

**Fluxos de Exceção:**
* **FA1:** O atendente tenta realizar check-out de uma placa que não foi registrada no sistema. → O sistema exibe erro e solicita nova verificação.
* **FA2:** O sistema falha ao calcular o valor (ex.: tarifa não configurada). → O atendente é notificado para informar ao gerente.
* **FA3:** O cliente não realiza o pagamento no caixa. → O check-out não pode ser concluído até o pagamento ser confirmado.

---

## 3. Caso de Uso: Gerar Relatórios

**Ator Principal:** Gerente

**Descrição:** O sistema deve fornecer relatórios de operação do estacionamento.

**Fluxo Principal:**
1. O gerente acessa a seção de relatórios.
2. O sistema apresenta os seguintes indicadores:
    * Frequência de clientes (quantidade de vezes que cada placa já estacionou).
    * Horários de pico (maior volume de check-ins).
    * Tempo médio de permanência (tempo total / número de veículos).
    * Faturamento diário (soma dos valores pagos).

**Fluxos de Exceção:**
* **FA1:** O gerente acessa os relatórios, mas não há registros no período selecionado. → O sistema exibe mensagem "Sem dados disponíveis para este período".
* **FA2:** O sistema não consegue gerar relatório por falha de conexão ou dados inconsistentes. → O gerente é notificado e solicitado a tentar novamente mais tarde.

---

## 4. Caso de Uso: Gerenciar Vagas

**Ator Principal:** Atendente / Gerente

**Descrição:** Permite visualizar e controlar a ocupação do estacionamento.

**Fluxo Principal:**
1. O sistema exibe as vagas disponíveis e ocupadas em um mapa do estacionamento.
2. Quando o estacionamento estiver lotado, o sistema envia uma notificação.
3. Quando houver vagas liberadas, o sistema atualiza automaticamente a disponibilidade.

**Fluxos de Exceção:**
* **FA1:** O sistema marca uma vaga como ocupada, mas o veículo sai sem fazer check-out. → O atendente pode corrigir manualmente a disponibilidade da vaga.
* **FA2:** O sistema notifica lotação máxima, mas após liberação de vagas, não atualiza o status automaticamente. → O atendente pode atualizar manualmente a lista de vagas.
