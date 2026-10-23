SNS vagy Simple Notification Center-ben lehetőségünk van riasztásokhoz beállítani email címet, így azonnali jelzéseket kaphatunk, ha a szerverünkél például magas CPU terhelés vagy egyéb hiba áll fent. 

<img width="1025" height="383" alt="Képernyőfotó 2026-10-19 - 14 02 14" src="https://github.com/user-attachments/assets/9abed4a4-0ced-4b96-8ffb-94a746c427ed" />

Létrehozunk egy topic-ot <mark>EC2-alarm<mark/> névvel.

<img width="1141" height="636" alt="Képernyőfotó 2026-10-19 - 14 02 46" src="https://github.com/user-attachments/assets/2f6315c5-a667-44e8-88cd-7a6b33d4da11" />

Megadjuk az email címet amire a riasztásokat szeretnénk kapni: 

<img width="1437" height="452" alt="Képernyőfotó 2026-10-19 - 14 04 18" src="https://github.com/user-attachments/assets/5d4cce0b-a402-44a4-8636-74b8f99ac22c" />

Ha befejeztük a konfigurálást akkor egy megerősítő email-t (confirmation) kapunk, amit mindenképpen aktiválnunk kell a működéshez

<img width="713" height="168" alt="Képernyőfotó 2026-10-19 - 14 04 42" src="https://github.com/user-attachments/assets/0edd1a4a-7dd1-4262-a681-9937ce0746de" />

Sikeres művelet esetén a következő fog megjelenni:

<img width="576" height="272" alt="Képernyőfotó 2026-10-19 - 14 04 56" src="https://github.com/user-attachments/assets/6bda6d1d-f33a-46b2-9333-459f911f085c" />

A feliratkozások `Subscription` részben ellenőrizhetjük, hogy tényleg visszaigazolt már az állapot

<img width="1165" height="196" alt="Képernyőfotó 2026-10-19 - 14 05 14" src="https://github.com/user-attachments/assets/17a3fb46-64c0-4aaf-8f5d-3a4949cb30a3" />
