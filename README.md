# saos10-netconf

This repository cointains config example for provisioning services and golden configs on:
* 5170 probably
* 5164s

## Configs are saved in the [goldens](goldens/) directory

### Copy config files FROM device

```bash
# Download running config
scp diag@10.92.44.150:/mnt/config/ciena-cfg.xml 5144-1.xml
```

### Copy config files TO device

1. Push file
  ```bash
  scp 5144-1.xml diag@10.92.44.150:/home/diag/foo.xml
  ```
2. login to device
  ```bash
  diag shell
  sudo cp /home/diag/foo.xml /mnt/config/.yumapro/backups/foo.xml
  exit
  conf reset user-config filename foo.xml
  ```
