CloudWatch agentet telepítünk az EC2 példányunkra, hogy a log fájlokat tudjuk naplózni és hibaüzenet esetén riasztást tudjunk beállítani rá. 

Első lépésként az EC2 példánynak hozzá kell rendelni az IAM role-hoz a `CloudWatchAgentServerPolicy`

Ezt létrehoztam IAM roleként és a Security fülnél már csak beállítottam a szerverre:

<img width="1449" height="345" alt="Képernyőfotó 2026-10-19 - 14 44 17" src="https://github.com/user-attachments/assets/5efd37cc-1b7e-4999-8d2f-20fa56b9c7eb" />

Ezután csatlakozunk a szerverünkhöz és telepítjük az agent-t.

Ehhez használhatjuk Linux esetén a következőt:
```bash
sudo yum install -y amazon-cloudwatch-agent
```
