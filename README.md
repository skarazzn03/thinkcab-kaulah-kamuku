#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

const char *lyrics[] = {
  "Siapapun yang", 
  "melihat kita",
  "mungkin kan",
  "mengerti",
  "dan membaca yang",
  "telah tersirat",
  "diantara kita"
};

const int durations[] = {
  1000,  // siapapun yang (1 detik)
  3000,  // melihat kita (3 detik)
  1000,  // mungkin kan (1 detik)
  2000,  // mengerti (2 detik)
  1000,  // dan membaca yang (1 detik)
  2000,  // telah tersirat (2 detik)
  2000   // di antara kita (2 detik)
};

int totalLines = sizeof(lyrics) / sizeof(lyrics[0]);

void setup() {
  lcd.init();          
  lcd.backlight();
  lcd.clear();
}

void loop() {
  for (int i = 0; i < totalLines; i++) {
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print(lyrics[i]); 
    delay(durations[i]);  
  }
}
