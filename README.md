**対応表**
赤が大文字青が小文字
![aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa](https://github.com/shuunnichi/aaaaaaaa/blob/main/ps4_1/messageImage_1709612485005.jpg)


***その他リンク***
>ps4のつなげ方等
https://404background.com/program/esp32-dualshock4/

>スケッチ大きすぎたとき
https://www.yagitech.jp/esp3218-%E3%82%B9%E3%82%B1%E3%83%83%E3%83%81%E3%81%8C%E5%A4%A7%E3%81%8D%E3%81%8F%E3%81%A6%E3%83%95%E3%83%A9%E3%83%83%E3%82%B7%E3%83%A5%E3%83%A1%E3%83%A2%E3%83%AA%E3%82%92%E8%B6%85%E3%81%88/

>コントローラー読み取るリンクhttps://github.com/hisa11/Hairo-Program-2023/blob/uaaaa/%E3%81%93%E3%82%93%E3%81%A8%E3%82%8D%E3%81%8A%E3%82%89%E3%81%82
**本文(古い）**
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
#if 0
  while (WiFi.status() != WL_CONNECTED) {
     delay(1000);
     Serial.println("つないでるぜ");
  }
#endif
  Serial.println("つながったぜ");
}

extern void print_and_udp(char *buf, char flag, int val);

void loop() {
  if (PS4.isConnected()) {
    if (PS4.Right()) print_and_udp("DDDDDDDDDD", 0, 0);
    if (PS4.Left()) print_and_udp("AAAAAAAAAA", 0, 0);
    if (PS4.Up()) print_and_udp("WWWWWWWWWW", 0, 0);
    if (PS4.Down()) print_and_udp("SSSSSSSSSS", 0, 0);
    if (PS4.Circle()) print_and_udp("dddddddddd", 0, 0);
    if (PS4.Square()) print_and_udp("aaaaaaaaaa", 0, 0);
    if (PS4.Triangle()) print_and_udp("wwwwwwwwww", 0, 0);
    if (PS4.Cross()) print_and_udp("ssssssssss", 0, 0);
    if (PS4.L1()) print_and_udp("kkkkkkkkkk", 0, 0);
    if (PS4.R1()) print_and_udp("yyyyyyyyyy", 0, 0);
    if (PS4.L3()) print_and_udp("2222222222", 0, 0);
    if (PS4.R3()) print_and_udp("3333333333", 0, 0);

    if (PS4.R2()) {
      int R2 = PS4.R2Value();
      if (R2 > 90) print_and_udp("hhhhhhhhhh", 0, 0);
    }
    if (PS4.L2()) {
      int L2 = PS4.L2Value();
      if (L2 > 90) print_and_udp("oooooooooo", 0, 0);
    }

    int gosa = 12;

    int Lx = PS4.LStickX();
    if (Lx < gosa && Lx > -gosa) {
      print_and_udp("L", 1, 0);
    } else {
      print_and_udp("L", 1, Lx);
    }
    int Ly = PS4.LStickY();
    if (Ly < gosa && Ly > -gosa) {
      print_and_udp("l", 1, 0);
    } else {
      print_and_udp("l", 1, Ly);
    }
    int Rx = PS4.RStickX();
    if (Rx < gosa && Rx > -gosa) {
      print_and_udp("R", 1, 0);
    } else {
      print_and_udp("R", 1, Rx);
    }
    int Ry = PS4.RStickY();
    if (Ry < gosa && Ry > -gosa) {
      print_and_udp("r", 1, 0);
    } else {
      print_and_udp("r", 1, Ry);
    }

    delay(10);
  }
}

void print_and_udp(char *buf, char flag, int val) {

  char buffer[16];
  if (flag) {
    sprintf(buffer, "%s%d", buf, val);
  } else {
    sprintf(buffer, "%s", buf);
  }
  Serial.printf(buffer);
  udp.beginPacket(IPAddress(192, 168, 8, 116), 1234);  // IP address and port of the receiver ESP32
  udp.print(buffer);
  udp.print("\n");
  Serial.printf("\n");
  udp.endPacket();
}
```

