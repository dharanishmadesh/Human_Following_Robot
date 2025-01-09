

# **Otto DIY Robot - Smart Movement and Obstacle Avoidance** 🤖🎉  

This repository contains the code for an **Otto DIY Robot** project, enhanced with obstacle detection, directional movement, and IR sensor integration. The robot uses ultrasonic and IR sensors to make intelligent navigation decisions.  

---

## **✨ Features**  

- **Ultrasonic Obstacle Detection**  
  - Detects obstacles within a 10cm range and moves forward or adjusts direction.  

- **IR Sensor Integration**  
  - Reads values from left and right IR sensors to detect objects and decide the turning direction.  

- **Custom Movements**  
  - Predefined functions for forward, backward, left, and right movements.  

- **Otto DIY Integration**  
  - Utilizes the Otto library for controlling servo motors and buzzer.  

---

## **📂 Folder Structure**  

- `Otto_Movement.ino`  
  - Main Arduino sketch file containing the robot's logic.  
- `README.md`  
  - Documentation for the project.  
- `LICENSE`  
  - Open-source license details (if applicable).  

---

## **🔧 Hardware Components**  

- **Otto DIY Robot Kit**  
  - Servos, body, and assembly parts.  
- **Ultrasonic Sensor** (e.g., HC-SR04)  
  - Trigger and Echo pins for distance measurement.  
- **IR Sensors**  
  - Left and right IR sensors for object detection.  
- **Arduino-Compatible Microcontroller**  
  - Board for running the robot's code.  
- **Buzzer**  
  - For audio feedback.  
- Jumper wires  
- Battery pack  

---

## **🔌 Circuit Connections**  

| Component       | Pin Assignment    |  
|------------------|-------------------|  
| **Left Leg**     | GPIO 2            |  
| **Right Leg**    | GPIO 3            |  
| **Left Foot**    | GPIO 4            |  
| **Right Foot**   | GPIO 5            |  
| **Ultrasonic Trigger** | GPIO 8      |  
| **Ultrasonic Echo**    | GPIO 9      |  
| **Left IR Sensor** | GPIO 7          |  
| **Right IR Sensor** | GPIO 6         |  
| **Buzzer**       | GPIO 13           |  

---

## **⚙️ Software Requirements**  

- Arduino IDE (version 1.8.10 or later)  
- Otto DIY Library ([Download here](https://github.com/OttoDIY/DIY))  

---

## **🚀 How to Use**  

1. **Setup**  
   - Assemble the Otto DIY Robot Kit.  
   - Connect the sensors and buzzer as per the circuit diagram above.  

2. **Upload Code**  
   - Open the `Otto_Movement.ino` file in Arduino IDE.  
   - Install the **Otto library** if not already done.  
   - Upload the code to your Arduino-compatible microcontroller.  

3. **Run the Robot**  
   - Power up the robot.  
   - Observe it navigate obstacles and respond to IR sensors.  

4. **Control Movements**  
   - Use predefined functions like `Forward()`, `Backward()`, `Left()`, `Right()`, and `Stop()` for manual control.  

---

## **💡 Code Overview**  

### **Ultrasonic Distance Measurement**  
```cpp
long ultrasound() {
   long duration, distance;
   digitalWrite(Trigger, LOW);
   delayMicroseconds(2);
   digitalWrite(Trigger, HIGH);
   delayMicroseconds(10);
   digitalWrite(Trigger, LOW);
   duration = pulseIn(Echo, HIGH);
   distance = duration / 58; // Convert to cm
   return distance;
}
```  

### **Directional Movements**  
- `Forward()`, `Backward()`, `Right()`, and `Left()` functions are used for navigation.  
- Obstacle detection logic determines movement based on sensor values:  
```cpp
if (ultrasound() <= 10) {
  Otto.walk(1, 1000, 1); // Move forward
} else if ((Left_Value == 0) && (Right_Value == 1)) {
  Otto.turn(3, 1000, 1); // Turn left
} else if ((Left_Value == 1) && (Right_Value == 0)) {
  Otto.turn(3, 1000, -1); // Turn right
}
```  

---

## **📜 License**  

This project is licensed under the **MIT License**. See the `LICENSE` file for details.  

---

## **🤝 Contributing**  

Contributions are welcome! Feel free to submit a pull request or open an issue for improvements or suggestions.  

---

## **💬 Feedback**  

For questions, suggestions, or feedback, feel free to reach out via the **Issues** section.  

---

Happy Building! 🎉
