**対応表**
!(https://github.com/shuunnichi/aaaaaaaa/blob/main/2024-02-24%20114515.png)
 
          



```
#include <WiFi.h>
#include <WiFiClient.h>
#include <WiFiAP.h>
#include <WiFiUdp.h>
#include <PS4Controller.h>


const char *ssid = "GL-SFT1200-19f";
const char *password = "goodlife";

WiFiUDP udp;




void setup() {
  Serial.begin(115200);
  PS4.begin("70:b8:f6:5c:80:16");
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("つないでるぜ");
  }

  Serial.println("つながったぜ");
}


void loop() {
  if (PS4.isConnected()) {
    if (PS4.Right()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "D");
      Serial.println("D");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.Left()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "A");
      Serial.println("A");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.Up()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "W");
      Serial.println("W");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.Down()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "S");
      Serial.println("S");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }

    if (PS4.Circle()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "d");
      Serial.println("d");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.Square()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "a");
      Serial.println("a");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.Triangle()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "w");
      Serial.println("w");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.Cross()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "s");
      Serial.println("s");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }


    if (PS4.LStickX()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "L%d\n", PS4.LStickX());  /////    L:leftx
      Serial.printf("L%d\n", PS4.LStickX());
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    } else {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "L0\n");
      Serial.printf("L0\n");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.LStickY()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "l%d\n", PS4.LStickY());  //   l:lefty
      Serial.printf("l%d\n", PS4.LStickY());
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    } else {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "l0\n");
      Serial.printf("l0\n");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.RStickX()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "R%d\n", PS4.RStickX());  //   R:rightx
      Serial.printf("R%d\n", PS4.RStickX());
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    } else {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "R0\n");
      Serial.printf("R0\n");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    if (PS4.RStickY()) {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "r%d\n", PS4.RStickY());  //   r:righty
      Serial.printf("r%d\n", PS4.RStickY());
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    } else {
      static int count = 0;
      char buffer[255];
      sprintf(buffer, "r0\n");
      Serial.printf("r0\n");
      udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
      udp.print(buffer);
      udp.print("\n");
      udp.endPacket();
    }
    // delay(100);
  }
}
```
//https://www.yagitech.jp/esp3218-%E3%82%B9%E3%82%B1%E3%83%83%E3%83%81%E3%81%8C%E5%A4%A7%E3%81%8D%E3%81%8F%E3%81%A6%E3%83%95%E3%83%A9%E3%83%83%E3%82%B7%E3%83%A5%E3%83%A1%E3%83%A2%E3%83%AA%E3%82%92%E8%B6%85%E3%81%88/

//https://github.com/hisa11/Hairo-Program-2023/blob/uaaaa/%E3%81%93%E3%82%93%E3%81%A8%E3%82%8D%E3%81%8A%E3%82%89%E3%81%82
