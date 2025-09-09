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

---

## 4. Caso de Uso: Gerenciar Vagas

**Ator Principal:** Atendente / Gerente

**Descrição:** Permite visualizar e controlar a ocupação do estacionamento.

**Fluxo Principal:**
1. O sistema exibe as vagas disponíveis e ocupadas em um mapa do estacionamento.
2. Quando o estacionamento estiver lotado, o sistema envia uma notificação.
3. Quando houver vagas liberadas, o sistema atualiza automaticamente a disponibilidade.
