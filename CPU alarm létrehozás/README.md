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

sudo dnf install -y stress-ng

stress-ng --cpu 2 --timeout 600s

<img width="814" height="129" alt="Képernyőfotó 2026-10-19 - 14 18 00" src="https://github.com/user-attachments/assets/f8a5a284-71e2-4c9d-8bed-a296a7f3acb5" />

parancsot beírva várunk, hogy mi történik a CPU használattal és kapunk-e riasztást
