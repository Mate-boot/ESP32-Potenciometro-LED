# Actividad Práctica ADC y PWM con ESP32

## Código desarrollado en Arduino IDE utilizando un ESP32, un potenciómetro y un LED para controlar la intensidad:

```.cpp
// ESP32 + Potenciómetro + LED
// Potenciómetro en GPIO 34
// LED en GPIO 2

const int potPin = 34;   // Entrada analógica
const int ledPin = 2;    // LED

int potValue = 0;        // Valor del potenciómetro
int brillo = 0;          // Brillo del LED

void setup() {
  pinMode(ledPin, OUTPUT);
  
  // Configuración PWM
  ledcAttach(ledPin, 5000, 8); 
  // GPIO, frecuencia 5kHz, resolución 8 bits
}

void loop() {

  // Leer potenciómetro (0 - 4095)
  potValue = analogRead(potPin);

  // Convertir a rango PWM (0 - 255)
  brillo = map(potValue, 0, 4095, 0, 255);

  // Encender LED con brillo variable
  ledcWrite(ledPin, brillo);

  delay(10);
}
```

## Video de la practica:
https://youtu.be/PoT_mvYgC2s
