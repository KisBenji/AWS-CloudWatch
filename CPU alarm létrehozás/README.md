A korábbi feladatokban létrehozott SNS feliratkozást fogjuk tesztelni és riasztást fogunk beállítani az EC2 példányunkra. A tesztet mesterséges CPU terheléssel fogjuk kipróbálni. 

ClouWatch-ban megnyitjuk az ALARM funkciót és `Create Alarm`-ra kattintva létrehozzuk az első riasztásunkat. 

<img width="1455" height="651" alt="Képernyőfotó 2026-10-19 - 14 05 55" src="https://github.com/user-attachments/assets/917b7957-bc97-40e1-9a24-700138446d02" />

Konfiguráljuk a riasztást a EC2 `CPUUtilization` metrikára a korábban létrehozott EC2-re.
Beállítjuk a tűréshatárt: 70%
In alarm → a korábban létrehozott SNS topicja Ec2-alarm

`Create alarm`

<img width="1449" height="706" alt="Képernyőfotó 2026-10-19 - 14 08 36" src="https://github.com/user-attachments/assets/35f40fe1-5dbb-4869-a610-ed27bbbb18cb" />
