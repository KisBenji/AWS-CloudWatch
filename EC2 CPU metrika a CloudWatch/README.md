Létrehozunk egy EC2 példányt Linux rendszerrel

A példa gép neve: <mark>server-cpu-cloudwatch<mark/>

A CPU metrikához szükséges beállításokhoz megnyitjuk a consol-ban a CloudWatch → Metrics → All Metrics → EC2 → Per-Instance Metrics

Itt tudjuk megkeresni a saját gépünkhöz tartozó `CPUUtilization`

<img width="1461" height="717" alt="Képernyőfotó 2026-10-19 - 13 56 31" src="https://github.com/user-attachments/assets/8c2ae4d0-0241-444e-b321-bacd4e7cfc8b" />

Grafikonon beállítjuk az utolsó 1 órát, hogy csak azt lássuk: Last 1 hour

<img width="1449" height="461" alt="Képernyőfotó 2026-10-19 - 13 59 31" src="https://github.com/user-attachments/assets/2ed6c512-ce7d-4549-8965-f86402412d13" />

Az EC2 CPU használata nyugalmi állapotban van. Nagyon alacsonyan 1% alatt.

<img width="1376" height="688" alt="Képernyőfotó 2026-10-19 - 14 01 03" src="https://github.com/user-attachments/assets/b412b1ca-036c-4c22-b34d-32383dc340ff" />
