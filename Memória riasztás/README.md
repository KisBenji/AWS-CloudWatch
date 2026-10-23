A következő tesztben azt nézzük meg, hogy a memória terhelésre hogyan tudunk beállítani a Cloudwatch Agent konfigurációját és alarm üzenetet küldeni a SNC regisztrációhoz.

Első körben csatlakozunk a szerverünkhöz és konfiguráljuk a json fájlt a memoria használat monitorozására:

<img width="450" height="403" alt="Képernyőfotó 2026-10-23 - 9 38 16" src="https://github.com/user-attachments/assets/46cb6852-5135-413f-bf1e-0259cd118459" />

Ezután létrehozunk egy metric filtert a memória használat monitorozására a korábbiak szerint és létrehozzuk az ALARM-ot is hozzá.

<img width="1470" height="956" alt="Képernyőfotó 2026-10-23 - 9 40 26" src="https://github.com/user-attachments/assets/518171c0-9fdd-4b53-900e-133c39f37883" />

A szerverünk memoria terhelését 95%-ra tesszük 2 percre:

<img width="777" height="109" alt="Képernyőfotó 2026-10-23 - 10 12 17" src="https://github.com/user-attachments/assets/ad412d60-de2d-4f00-8b98-67f88f915366" />

Egy perc elteltével látjuk, hogy a beállított 50%-os határérték felé ment a terhelés hatására és in ALARM-ba lépett a státusz.

<img width="1164" height="502" alt="Képernyőfotó 2026-10-23 - 10 11 01" src="https://github.com/user-attachments/assets/a49fd984-4489-48c8-9367-8a6fada5d676" />

A beállított riasztáshoz hozzárendelt SNC miatt email-es riasztást is kapunk.

<img width="708" height="634" alt="Képernyőfotó 2026-10-23 - 10 11 35" src="https://github.com/user-attachments/assets/006ef120-5d65-4d37-845e-1e523ecd907b" />

Két per elteltével a mesterséges memoria terhelésnek vége és újra "normális" állapotba kerül a szerver:

<img width="1180" height="479" alt="Képernyőfotó 2026-10-23 - 10 13 47" src="https://github.com/user-attachments/assets/6c2d6609-a73f-4f5d-898c-640fd1eeeaa8" />

Természetesen email-es értesítés is követi, hogy megszűnt a riasztás és már OK minden.

<img width="713" height="648" alt="Képernyőfotó 2026-10-23 - 10 14 01" src="https://github.com/user-attachments/assets/d63c250a-7c4b-4206-a409-1c272bafbdc7" />
