const int pin_Reset = 16;
const int pin_1_Pesos = 5;
const int pin_2_Pesos = 14;
const int pin_5_Pesos = 12;
const int pin_10_Pesos = 13;
const int pin_20_Pesos = 15;

int counter_1_pesos;
int counter_2_pesos;
int counter_5_pesos;
int counter_10_pesos;
int counter_20_pesos;

bool estado_anterior_reset = HIGH;
bool estado_anterior_1_Pesos = HIGH;
bool estado_anterior_2_Pesos = HIGH;
bool estado_anterior_5_Pesos = HIGH;
bool estado_anterior_10_Pesos = HIGH;
bool estado_anterior_20_Pesos = HIGH;

unsigned long tiempoUltimoEvento = 0;
const unsigned long debounceDelay = 200; //200 ms para evitar rebotes

void setup() {
  Serial.begin(9600);
  pinMode(pin_Reset, INPUT_PULLUP); //Reset Buton
  pinMode(pin_1_Pesos, INPUT_PULLUP); //$1 Coin
  pinMode(pin_2_Pesos, INPUT_PULLUP); //$2 Coin
  pinMode(pin_5_Pesos, INPUT_PULLUP); //$5 Coin
  pinMode(pin_10_Pesos, INPUT_PULLUP); //$10 Coin
  pinMode(pin_20_Pesos, INPUT_PULLUP); //$20 Coin
}

void loop() {

  unsigned long tiempoActual = millis();

  int estado_reset = digitalRead(pin_Reset); //D0 RESET
  int estado_1_pesos = digitalRead(pin_1_Pesos); //D1 $1 Pesos
  int estado_2_pesos = digitalRead(pin_2_Pesos); //D5 $2 Pesos
  int estado_5_pesos = digitalRead(pin_5_Pesos); //D6 $5 Pesos
  int estado_10_pesos = digitalRead(pin_10_Pesos); //D7 $10 Pesos
  int estado_20_pesos = digitalRead(pin_20_Pesos); //D8 $20 Pesos

  if (tiempoActual - tiempoUltimoEvento > debounceDelay){
    //Comando para reset de los contadores
    if (estado_anterior_reset == HIGH && estado_reset == LOW){
      counter_1_pesos = 0;
      counter_2_pesos = 0;
      counter_5_pesos = 0;
      counter_10_pesos = 0;
      counter_20_pesos = 0;
      Serial.print("Valores reseteados");
      tiempoUltimoEvento = tiempoActual;
    }
  

    //Comando para monedas de un pesos
    if (estado_anterior_1_Pesos == HIGH && estado_1_pesos == LOW){
      counter_1_pesos++;
      tiempoUltimoEvento = tiempoActual;
    }

    //Comando para monedas de dos pesos
    if (estado_anterior_2_Pesos == HIGH && estado_2_pesos == LOW){
      counter_2_pesos++;
      tiempoUltimoEvento = tiempoActual;
    }

    //Comando para monedas de cinco pesos
    if (estado_anterior_5_Pesos == HIGH && estado_5_pesos == LOW){
      counter_5_pesos++;
      tiempoUltimoEvento = tiempoActual;
    }

    //Comando para monedas de diez pesos
    if (estado_anterior_10_Pesos == HIGH && estado_10_pesos == LOW){
      counter_10_pesos++;
      tiempoUltimoEvento = tiempoActual;
    }

    //Comando para monedas de veinte pesos
    if (estado_anterior_20_Pesos == HIGH && estado_20_pesos == LOW){
      counter_20_pesos++;
      tiempoUltimoEvento = tiempoActual;
    }
  }
  

  //Actualizar el valor de los estados con la ultima entrada
  estado_anterior_reset = estado_reset;
  estado_anterior_1_Pesos = estado_1_pesos;
  estado_anterior_2_Pesos = estado_2_pesos;
  estado_anterior_5_Pesos = estado_5_pesos;
  estado_anterior_10_Pesos = estado_10_pesos;
  estado_anterior_20_Pesos = estado_20_pesos;

  if (Serial.available() > 0){
    char tecla = Serial.read();
    if (tecla == 'a'){
      Serial.println("Los valores guardados son:");
      Serial.print("Contador de $1: ");
      Serial.println(counter_1_pesos);

      Serial.print("Contador de $2: ");
      Serial.println(counter_2_pesos);

      Serial.print("Contador de $5: ");
      Serial.println(counter_5_pesos);

      Serial.print("Contador de $10: ");
      Serial.println(counter_10_pesos);

      Serial.print("Contador de $20: ");
      Serial.println(counter_20_pesos);
    }
  }
}
