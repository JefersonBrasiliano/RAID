## Laboratório Multi-RAID - Configuração de RAID 0, 1 e 5 na mesma máquina virtual

## 🎯 Objetivo do Projeto

Construir uma única máquina virtual Linux que implemente **três níveis diferentes de RAID simultaneamente**:

| RAID | Nível | Discos | Tamanho útil | Finalidade |
|------|-------|--------|--------------|-------------|
| /dev/md0 | **RAID 0** | sdb1 + sdc1 | ~20 GB | Desempenho máximo |
| /dev/md1 | **RAID 1** | sdd1 + sde1 | ~10 GB | Tolerância a falhas |
| /dev/md2 | **RAID 5** | sdf1 + sdg1 + sdh1 | ~20 GB | Equilíbrio desempenho/segurança |

## 🖥️ Ambiente utilizado

- **Virtualização**: Oracle VirtualBox
- **Sistema Operacional**: Slax Linux 6.0.7 (Developer Edition)
- **Discos**: 1 disco base (SO) + 7 discos de 10 GB para os RAIDs
- **Ferramentas**: fdisk, mdadm, mkfs.ext3

## 📋 Especificações do projeto
Máquina Virtual Multi-RAID
├── Controladora SATA<p></p>
│ ├── sda - Disco do sistema (Slax)<p></p>
│ ├── sdb - 10 GB → RAID 0 (parte 1)<p></p>
│ ├── sdc - 10 GB → RAID 0 (parte 2)<p></p>
│ ├── sdd - 10 GB → RAID 1 (parte 1)<p></p>
│ ├── sde - 10 GB → RAID 1 (parte 2)<p></p>
│ ├── sdf - 10 GB → RAID 5 (parte 1)<p></p>
│ ├── sdg - 10 GB → RAID 5 (parte 2)<p></p>
│ └── sdh - 10 GB → RAID 5 (parte 3)<p></p>
