CloudWatch agentet telepítünk az EC2 példányunkra, hogy a log fájlokat tudjuk naplózni és hibaüzenet esetén riasztást tudjunk beállítani rá. 

Első lépésként az EC2 példánynak hozzá kell rendelni az IAM role-hoz a `CloudWatchAgentServerPolicy`

Ezt létrehoztam IAM roleként és a Security fülnél már csak beállítottam a szerverre:

<img width="1449" height="345" alt="Képernyőfotó 2026-10-19 - 14 44 17" src="https://github.com/user-attachments/assets/5efd37cc-1b7e-4999-8d2f-20fa56b9c7eb" />

Ezután csatlakozunk a szerverünkhöz és telepítjük az agent-t.

Ehhez használhatjuk Linux esetén a következőt:
```bash
sudo yum install -y amazon-cloudwatch-agent
```
<img width="1463" height="716" alt="Képernyőfotó 2026-10-19 - 14 47 00" src="https://github.com/user-attachments/assets/79d8e06e-0820-4b56-88e0-d1369f627956" />

Ezután konfiguráljuk az agent-t a `/var/log/messages` fájlra, log group `/ec2/messages` -re. Ezt egy konfigurációs fájlt kell létrehoznunk json formátumban.

A következő parancsokat tudjuk beírni a konfigurációs fájl betápláláshoz:
```bash
sudo mkdir -p /opt/aws/amazon-cloudwatch-agent/etc
sudo nano /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json
```
A megnyílt szerkesztőbe tudjuk a json fájlunkat bemásolni:
```bash

{
  "logs": {
    "logs_collected": {
      "files": {
        "collect_list": [
          {
            "file_path": "/var/log/messages",
            "log_group_name": "/ec2/messages",
            "log_stream_name": "i-0aa94f1d833439c02",
            "timezone": "Local"
          }
        ]
      }
    }
  }
}
```
<img width="1252" height="319" alt="Képernyőfotó 2026-10-19 - 15 51 26" src="https://github.com/user-attachments/assets/ceb6c6d5-6245-48e9-b788-7172e6cf9ba2" />

Itt a file path lesz a beállított log fájlok. A log group name az Ec2/message elnevezést kapja. A stream neve az EC2 ID-ja. 

Ezután már készen áll az agent az indításra:
```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
  -a fetch-config \
  -m ec2 \
  -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json \
  -s
```

