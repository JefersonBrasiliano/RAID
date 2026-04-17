Laboratório de Configuração RAID no Linux (Slax)
 Projeto desenvolvido a partir da disciplina Arquitetura de Alto Desempenho para Banco de Dados (UNICAMP), ministrada pelo Prof. José Luís Zem.

Este repositório documenta a configuração de diferentes níveis de RAID (0, 1 e 5) 
em máquinas virtuais Linux (Slax 6.0.7) rodando no Oracle VirtualBox.

## Ambientes configurados

- **RAID 0 (Striping)** - 2 discos de 10GB
- **RAID 1 (Mirroring)** - 2 discos de 10GB  
- **RAID 5 (Paridade distribuída)** - 3 discos de 10GB

## Ferramentas utilizadas

- Oracle VirtualBox
- Slax Linux 6.0.7
- fdisk
- mdadm
- mkfs.ext3

## Comandos executados


```bash
# Criar partições
fdisk /dev/sdb  # tipo fd (Linux RAID Auto)
fdisk /dev/sdc  # tipo fd

# Criar o RAID
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

# Criar sistema de arquivos
mkfs.ext3 /dev/md0

# Montagem automática no boot
echo "mount /dev/md0 /raid1" >> /etc/rc.d/rc.local
Resultados
RAID 0: ~20GB úteis, desempenho melhorado

RAID 1: ~10GB úteis, tolerância a falha de 1 disco

RAID 5: ~20GB úteis, tolerância a falha de 1 disco
```
Para baixar o appliance, [clique aqui](https://unicampbr-my.sharepoint.com/:u:/g/personal/ex198175_m_unicamp_br/IQC1p59RPN9OTJRNFtbTMU1mAfoSkfpeoT-lQjj6l4CtA_M?e=Ncwgc8)

<p></p>
<img width="1304" height="119" alt="image" src="https://github.com/user-attachments/assets/85686d1e-48c7-4b47-82b1-78d2a3bdfac7" />

