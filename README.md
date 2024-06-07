# GS-Edge-Computing

Feito por Guilherme Melo (555310) e Matheus Gushi (556935).

Descrição:

  Este projeto utiliza um microcontrolador Arduino para monitorar a qualidade da água através de sensores de temperatura, turbidez, TDS (Sólidos Dissolvidos Totais) e pH. 
  Os dados coletados são exibidos em um display LCD I2C e também enviados para a porta serial. O sistema avalia a qualidade da água e exibe uma mensagem indicando se ela é segura para uso doméstico ou perigosa.

Funcionalidades:

  Leitura de sensores de temperatura, turbidez, TDS e pH.
  Exibição dos valores dos sensores em um display LCD I2C.
  Envio dos dados dos sensores para a porta serial.
  Avaliação da qualidade da água e exibição de uma mensagem de status.

Montagem do Circuito:

  Conecte o sensor de temperatura ao pino analógico A0.
  Conecte o sensor de turbidez ao pino analógico A1.
  Conecte o sensor de TDS ao pino digital 2.
  Conecte o sensor de pH ao pino digital 3.
  Conecte o display LCD I2C ao barramento I2C do Arduino.

Carregamento do Código:

  Instale a biblioteca LiquidCrystal_I2C através do Gerenciador de Bibliotecas do Arduino IDE.
  Copie e cole o código fornecido na IDE do Arduino.
  Compile e faça o upload do código para o Arduino.

Operação:

  Após o upload do código, o sistema iniciará automaticamente.
  Os valores dos sensores serão exibidos no display LCD I2C e enviados para a porta serial.
  A cada 2 segundos, os valores dos sensores serão atualizados no display LCD.
  O status da qualidade da água será mostrado no display LCD: "DOMESTIC USE" (uso doméstico seguro) ou "DANGEROUS" (perigoso).

Requisitos:

  Hardware:
  
    Arduino (qualquer modelo compatível, ex. Arduino Uno)
    Sensor de Temperatura (ex. LM35)
    Sensor de Turbidez
    Sensor de TDS
    Sensor de pH
    Display LCD 16x2 com interface I2C
    Cabos jumpers e protoboard para conexões
  
  Software:
  
    Arduino IDE
    Biblioteca LiquidCrystal_I2C (pode ser instalada via Gerenciador de Bibliotecas do Arduino IDE)
    Dependências
    Biblioteca LiquidCrystal_I2C:
    cpp
  


