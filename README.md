# 🍷 Sistema de Monitoramento de Iluminação - Vinheria Agnello

Este projeto foi desenvolvido para a Vinheria Agnello como parte de um sistema de monitoramento ambiental para garantir as condições ideais de armazenamento de vinhos. O foco inicial é no controle da luminosidade, um dos três fatores críticos (juntamente com temperatura e umidade) que afetam a qualidade dos vinhos.

##  📋 Descrição

O projeto monitora a intensidade da luz ambiente usando um sensor LDR (Light Dependent Resistor). Dependendo da luminosidade detectada, o sistema faz as seguintes ações:

- **LED verde acende** quando o nível de luz é baixo (segurança alta).
- **LED amarelo acende** quando o nível de luz está moderado (em atenção).
- **LED vermelho acende** quando o nível de luz é crítico (nível de atenção máximo).
  
O buzzer emite um som de 3 segundos para níveis de luz moderados. O som é repetido a cada 5 segundos enquanto os níveis de luz permanecem em alerta.
No nível crítico, o alerta é apenas visual com o LED vermelho.

###  🌟 Objetivo do projeto:

- **Monitorar e controlar a iluminação de um ambiente**, acionando alertas visuais e sonoros.
- **Ajustar os LEDs** para diferentes estados de iluminação.
- **Emissão de som** para alertar sobre níveis de atenção.

## 🧩 Componentes Necessários

### 💻 Hardware
| Componente       | Quantidade | Especificações          |
|------------------|------------|-------------------------|
| Arduino Uno      | 1          | Placa controladora      |
| Sensor LDR       | 1          | Fotoresistor 5mm        |
| LED Verde        | 1          | 5mm, 20mA               |
| LED Amarelo      | 1          | 5mm, 20mA               |
| LED Vermelho     | 1          | 5mm, 20mA               |
| Buzzer           | 1          | Ativo, 5V               |
| Resistor 10kΩ    | 1          | Para divisor de tensão  |
| Resistor 220Ω    | 3          | Proteção para LEDs      |
| Resistor 100Ω    | 1          | Proteção para o buzzer  |

### 📲 Software
- Arduino IDE 2.0+
- Biblioteca padrão (sem dependências externas)

## 🔧 Montagem do Circuito

### 📌 Diagrama de Conexões
```circuit
[+5V]──[LDR]───[A3]
             │
            [10kΩ]
             │
            [GND]

[Pino 2]──[220Ω]──[LED Verde]──[GND]  
[Pino 3]──[220Ω]──[LED Amarelo]──[GND]  
[Pino 4]──[220Ω]──[LED Vermelho]──[GND]  
[Pino 13]──[100Ω]──[Buzzer +]  
[GND]────────────[Buzzer -]
```

1. **Montagem do circuito:**
   - Conecte o LDR entre o pino analógico A3 e o VCC (5V). Use um resistor de 10kΩ entre o pino A3 e o GND para formar um divisor de tensão.
   - Conecte os LEDs nos pinos digitais 2, 3 e 4, com resistores de 220Ω em série.
   - Conecte o buzzer ao pino digital 13 com um resistor de 100Ω em série para limitar corrente e proteger o componente.

2. **Instalar a IDE do Arduino:**
   - Baixe e instale a [Arduino IDE](https://www.arduino.cc/en/software).
   - Abra a IDE e selecione a placa e a porta serial corretas no menu **Ferramentas**.

3. **Carregar o código no Arduino:**
   - Abra a IDE do Arduino.
   - Crie um novo arquivo e cole o código fornecido no início do README.
   - Selecione a placa correta (**Arduino Uno**) em **Ferramentas > Placa**.
   - Selecione a porta serial correta em **Ferramentas > Porta**.
   - Clique em **Carregar** para enviar o código para o seu Arduino.

4. **Monitoramento de Lux:**
   - Após o código ser carregado, o Arduino começará a medir o valor de luz com o LDR.
   - O valor de lux será impresso no monitor serial da IDE do Arduino. Isso permitirá verificar os níveis de iluminação detectados.

5. **Testando o alarme:**
   - Ajuste a luz no ambiente onde o LDR está posicionado. O sistema acenderá os LEDs e emitirá um alarme de acordo com o nível de luminosidade.
   - A cada 5 segundos, o buzzer emitirá um som, dependendo do nível de luz.

## 🧠 Funcionamento do Código

- O código utiliza a função `analogRead()` para ler o valor da intensidade da luz do LDR.
- A variável `lux` é calculada com base no valor do LDR e convertida para lux utilizando a equação fornecida de acordo com a documentação do Wokwi([Doc Wokwi](https://docs.wokwi.com/pt-BR/parts/wokwi-photoresistor-sensor)). 
- O código define dois limites para a luminosidade:
  - **Limite de Lux (`limite_lux`)**: Quando a luminosidade está abaixo deste valor, o LED verde acende. 
  - **Limite de Atenção (`atencao_lux`)**: Quando a luminosidade excede este valor, o LED vermelho acende para indicar o ponto crítico.
  - **Intervalo (`atencao_lux` - `limite_lux`)**: Quando a luminosidade está entre o limite de lux e o limite de atenção, o LED amarelo acende e um aviso sonoro é emitido em um intervalo de 3 segundos para indicar o nível de alerta.

## 🌐 Recursos Adicionais
[**Documentação do Sensor LDR**](https://docs.wokwi.com/pt-BR/parts/wokwi-photoresistor-sensor)<br>
[**Wokwi**](https://wokwi.com/projects/428977194488305665)

## Integrantes
Matheus von Koss Wildeisen - RM: 561539<br>
Ana Clara Rocha de Oliveira – RM: 564298<br>
Joao Nishikawa – RM: 562376<br>
Deivid ruan Marques – RM: 566356<br>
Felipe Cordeiro RM: 566518<br>
