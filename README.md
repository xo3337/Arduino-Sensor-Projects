
# 🤖 Arduino Sensor Projects

This document contains **two Arduino tasks** demonstrating the use of analog and digital sensors:

- **Task 1**: PIR Motion Sensor – Detect motion and light an LED
- **Task 2**: Flex Sensor – Detect bending and light an LED

---

## 🧪 Task 1: Motion Detection with PIR Sensor

### 🔌 Circuit Diagram

<img width="253" height="323" alt="image" src="https://github.com/user-attachments/assets/7f22d700-c372-460d-a814-f8967fda916f" />


### 🔧 Components

- Arduino Uno
- PIR Motion Sensor (HC-SR501)
- LED
- 220Ω Resistor
- Breadboard + Jumper Wires

### ⚙️ Wiring

| PIR Sensor Pin | Connects To         |
|----------------|---------------------|
| VCC            | 5V                  |
| GND            | GND                 |
| OUT            | Arduino Digital Pin 2 |

| LED Pin     | Connects To             |
|-------------|--------------------------|
| Anode (+)   | Digital Pin 13 (with resistor) |
| Cathode (−) | GND                      |

### 📜 Code

```cpp
int pirPin = 2;       // PIR sensor output pin
int ledPin = 13;      // LED pin

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int motion = digitalRead(pirPin);

  if (motion == HIGH) {
    digitalWrite(ledPin, HIGH);
    Serial.println("Motion detected!");
  } else {
    digitalWrite(ledPin, LOW);
    Serial.println("No motion.");
  }

  delay(200);
}
```

---

## 🧪 Task 2: Flex Sensor Input

### 🔌 Circuit Diagram

<img width="383" height="495" alt="image" src="https://github.com/user-attachments/assets/9053f7f9-1ba3-462c-96b3-c3551ba6eee4" />


### 🔧 Components

- Arduino Uno
- Flex Sensor
- LED
- 10kΩ Resistor (pull-down for analog reading)
- 220Ω Resistor (for LED)
- Breadboard + Jumper Wires

### ⚙️ Wiring

| Flex Sensor Pin | Connects To                  |
|------------------|------------------------------|
| End 1            | 5V                           |
| End 2            | A0 + GND through 10kΩ resistor |

| LED Pin     | Connects To             |
|-------------|--------------------------|
| Anode (+)   | Digital Pin 8 (via 220Ω) |
| Cathode (−) | GND                      |

### 📜 Code

```cpp
int sensor = 0;

void setup() {
  pinMode(A0, INPUT);
  pinMode(8, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  sensor = analogRead(A0);

  if (sensor < 20) {
    digitalWrite(8, HIGH);
  } else {
    digitalWrite(8, LOW);
  }

  Serial.print("Flex sensor reading = ");
  Serial.println(sensor);
  delay(100);
}
```

---

## 🛠️ Summary

| Task | Sensor Type | Input Type | Output       |
|------|-------------|------------|--------------|
| 1    | PIR Sensor  | Digital    | LED + Serial |
| 2    | Flex Sensor | Analog     | LED + Serial |

---

## 📄 License

Open-source under the MIT License. Use freely for learning and development.
