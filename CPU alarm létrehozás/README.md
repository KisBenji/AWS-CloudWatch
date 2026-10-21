A korábbi feladatokban létrehozott SNS feliratkozást fogjuk tesztelni és riasztást fogunk beállítani az EC2 példányunkra. A tesztet mesterséges CPU terheléssel fogjuk kipróbálni. 

ClouWatch-ban megnyitjuk az ALARM funkciót és `Create Alarm`-ra kattintva létrehozzuk az első riasztásunkat. 

<img width="1455" height="651" alt="Képernyőfotó 2026-10-19 - 14 05 55" src="https://github.com/user-attachments/assets/917b7957-bc97-40e1-9a24-700138446d02" />

Konfiguráljuk a riasztást a EC2 `CPUUtilization` metrikára a korábban létrehozott EC2-re.
Beállítjuk a tűréshatárt: 70%

<img width="1449" height="706" alt="Képernyőfotó 2026-10-19 - 14 08 36" src="https://github.com/user-attachments/assets/35f40fe1-5dbb-4869-a610-ed27bbbb18cb" />

In alarm → a korábban létrehozott SNS topicja Ec2-alarm

<img width="1155" height="582" alt="Képernyőfotó 2026-10-19 - 14 08 55" src="https://github.com/user-attachments/assets/4d578f26-cf0e-470f-a717-38e2b908607d" />

A következőt kell látnunk a létrehozás után:

<img width="1190" height="467" alt="Képernyőfotó 2026-10-19 - 14 11 43" src="https://github.com/user-attachments/assets/a68ee234-c41e-476a-a13c-fd3d560f273e" />

Egyelőre az EC2 példány nyugalmi állapotban az OK állapotban van.

Generáljunk mesterségesen magas CPU használatot! 
Csatlakozunk az EC2 gépünkhöz és a 

```bash
sudo dnf install -y stress-ng
stress-ng --cpu 2 --timeout 600s
```

<img width="814" height="129" alt="Képernyőfotó 2026-10-19 - 14 18 00" src="https://github.com/user-attachments/assets/f8a5a284-71e2-4c9d-8bed-a296a7f3acb5" />

parancsot beírva várunk, hogy mi történik a CPU használattal és kapunk-e riasztást!?

Pár perc elteltével a következő grafikont láthatjuk, ha jól írtunk be mindent: 

<img width="1188" height="600" alt="Képernyőfotó 2026-10-19 - 14 18 35" src="https://github.com/user-attachments/assets/503938ca-a9fa-4831-9d44-284f5c72499f" />

A rendszer pár perc elteltével email-t is küld a hibával, hogy OK->ALARM állapotba került a szerverünk. Így most már biztosak lehetünk, hogy jól állítottuk be az SNC beállításait.

<img width="707" height="689" alt="Képernyőfotó 2026-10-19 - 14 16 42" src="https://github.com/user-attachments/assets/f3481688-31e5-47ab-82e1-37e451fb9def" />

A teszt végén teszteljük, ha leállítjuk a terhelést akkor megszűnik-e a riasztás és újabb levelet kapunk-e arról, hogy az állapota a szervernek ALARM->OK lett.

A terhelés leállításához a következő kódot használhatjuk: 

```bash
sudo pkill stress-ng
```

<img width="569" height="49" alt="Képernyőfotó 2026-10-19 - 14 23 20" src="https://github.com/user-attachments/assets/250b6378-00bb-485f-aebb-329a15650ab7" />

Pár perc elteltével a CPU terhelés a beállított határérték alá csökken:

<img width="1202" height="602" alt="Képernyőfotó 2026-10-19 - 14 26 12" src="https://github.com/user-attachments/assets/74f17177-075e-4be2-9ede-62bd011a5d87" />

A rendszer küld megerősíti emailben is, hogy most már minden megfelelő:

<img width="749" height="658" alt="Képernyőfotó 2026-10-19 - 14 41 40" src="https://github.com/user-attachments/assets/fc1c4eb4-b6b0-4643-bf24-bafa241ce50a" />
