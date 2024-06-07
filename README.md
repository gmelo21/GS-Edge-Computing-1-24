# GS-Edge-Computing

Feito por Guilherme Melo (555310) e Matheus Gushi (556935).

YouTube - https://youtu.be/CxBKUAdqvjM
Tinkercad - https://www.tinkercad.com/things/kF8TzcOwSyk-water-quality-control

Código:

    #include <LiquidCrystal_I2C.h>
    
    // Definições de endereço I2C e configurações do LCD
    #define I2C_ADDR    0x27
    #define LCD_COLUMNS 16
    #define LCD_LINES   2
    
    // Inicialização do LCD
    LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);
    
    // Declaração de funções
    void displayMessage(bool situationSafe, LiquidCrystal_I2C &lcd);
    
    // Variáveis globais
    int sensorTempPin = 14;
    int sensorTurbPin = A1;
    int sensorTDSPin = 2;
    int sensorPHPin = 3;
    
    void setup() {
      // Inicialização do LCD e porta serial
      lcd.init();
      lcd.backlight();
      Serial.begin(9600);
    }
    
    void loop() {
      // Configuração de pinos para sensores
      pinMode(sensorTempPin, INPUT);
      float temp = map(analogRead(sensorTempPin), 20, 358, -40, 125);
    
      pinMode(sensorTurbPin, INPUT);
      int turb;
      int TUR1;
      turb = analogRead(sensorTurbPin);
      TUR1 = map(turb, 0, 471, 0, 5);
    
      pinMode(sensorTDSPin, INPUT);
      int TDS;
      int TDS1;
      TDS = analogRead(sensorTDSPin);
      TDS1 = map(TDS, 0, 1023, 0, 2000);
    
      pinMode(sensorPHPin, INPUT);
      int PH;
      int PH1;
      PH = analogRead(sensorPHPin);
      PH1 = map(PH, 0, 1023, 0, 14);
      
      // Verifica se a situação é segura com base nos valores dos sensores
      bool situationSafe = (TUR1 >= 4 && TDS < 600 && (PH1 >= 6.5 && PH1 <= 7));
    
      // Limpa o LCD e imprime os valores dos sensores
      lcd.clear();
      Serial.print("TEMPERATURE:"); 
      Serial.println(temp);
      Serial.print("TURBIDITY:"); 
      Serial.println(TUR1);
      Serial.print("TDS:");
      Serial.println(TDS1);
      Serial.print("PH:");
      Serial.println(PH1);
    
      // Mostra os valores no LCD e exibe a mensagem correspondente
      lcd.setCursor(1, 0); 
      lcd.print("TEMP");
      lcd.setCursor(7, 0); 
      lcd.print(temp);
      displayMessage(situationSafe, lcd);
      delay(2000);
      lcd.clear();
    
      lcd.setCursor(1, 0); 
      lcd.print("TURB");
      lcd.setCursor(7, 0); 
      lcd.print(TUR1);
      displayMessage(situationSafe, lcd);
      delay(2000);
      lcd.clear();
    
      lcd.setCursor(1, 0); 
      lcd.print("PH");
      lcd.setCursor(7, 0); 
      lcd.print(PH1);
      displayMessage(situationSafe, lcd);
      delay(2000);
      lcd.clear();
    
      lcd.setCursor(1, 0); 
      lcd.print("TDS");
      lcd.setCursor(7, 0); 
      lcd.print(TDS1);
      displayMessage(situationSafe, lcd);
      delay(2000);
      lcd.clear();
    }
    
    // Função para exibir a mensagem correspondente com base na situação segura
    void displayMessage(bool situationSafe, LiquidCrystal_I2C &lcd) {
      lcd.setCursor(1, 1);
      if (situationSafe) {
        lcd.print("DOMESTIC USE");
      } else {
        lcd.print("DANGEROUS");
      }
    }

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
  


