
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
