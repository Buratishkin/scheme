# Паспорт системы

---

## 1. Ядро и архитектура

Команда:

```bash
uname -a
```

<details>
<summary>Вывод команды</summary>

```text
Linux buratishkin 6.14.0-24-generic #24~24.04.3-Ubuntu SMP PREEMPT_DYNAMIC Mon Jul  7 16:39:17 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

</details>

---

## 2. Информация о процессоре

Команда:

```bash
lscpu
```

<details>
<summary>Вывод команды</summary>

```text
Архитектура:              x86_64
  CPU op-mode(s):         32-bit, 64-bit
  Address sizes:          39 bits physical, 48 bits virtual
  Порядок байт:           Little Endian
CPU(s):                   20
  On-line CPU(s) list:    0-19
ID прроизводителя:        GenuineIntel
  Имя модели:             13th Gen Intel(R) Core(TM) i7-13650HX
    Семейство ЦПУ:        6
    Модель:               183
    Потоков на ядро:      2
    Ядер на сокет:        14
    Сокетов:              1
    Степпинг:             1
    CPU(s) scaling MHz:   42%
    CPU max MHz:          2600,0000
    CPU min MHz:          800,0000
    BogoMIPS:             5606,40
    Флаги:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge m
                          ca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 s
                          s ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc 
                          art arch_perfmon pebs bts rep_good nopl xtopology nons
                          top_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq 
                          dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 
                          xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_d
                          eadline_timer aes xsave avx f16c rdrand lahf_lm abm 3d
                          nowprefetch cpuid_fault epb ssbd ibrs ibpb stibp ibrs_
                          enhanced tpr_shadow flexpriority ept vpid ept_ad fsgsb
                          ase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed
                           adx smap clflushopt clwb intel_pt sha_ni xsaveopt xsa
                          vec xgetbv1 xsaves split_lock_detect user_shstk avx_vn
                          ni dtherm arat pln pts hwp hwp_notify hwp_act_window h
                          wp_epp hwp_pkg_req hfi vnmi umip pku ospke waitpkg gfn
                          i vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clea
                          r serialize arch_lbr ibt flush_l1d arch_capabilities
Virtualization features:  
  Виртуализация:          VT-x
Caches (sum of all):      
  L1d:                    544 KiB (14 instances)
  L1i:                    704 KiB (14 instances)
  L2:                     11,5 MiB (8 instances)
  L3:                     24 MiB (1 instance)
NUMA:                     
  NUMA node(s):           1
  NUMA node0 CPU(s):      0-19
Vulnerabilities:          
  Gather data sampling:   Not affected
  Ghostwrite:             Not affected
  Itlb multihit:          Not affected
  L1tf:                   Not affected
  Mds:                    Not affected
  Meltdown:               Not affected
  Mmio stale data:        Not affected
  Reg file data sampling: Mitigation; Clear Register File
  Retbleed:               Not affected
  Spec rstack overflow:   Not affected
  Spec store bypass:      Mitigation; Speculative Store Bypass disabled via prct
                          l
  Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointe
                          r sanitization
  Spectre v2:             Mitigation; Enhanced / Automatic IBRS; IBPB conditiona
                          l; PBRSB-eIBRS SW sequence; BHI BHI_DIS_S
  Srbds:                  Not affected
  Tsx async abort:        Not affected
```

</details>

---

## 3. Топология процессора

Команда:

```bash
lscpu -e
```

Показывает соответствие logical CPU, physical core и socket. Полезно для анализа SMT и использования `taskset`.

<details>
<summary>Вывод команды</summary>

```text
CPU NODE SOCKET CORE L1d:L1i:L2:L3 ONLINE    MAXMHZ   MINMHZ       MHZ
  0    0      0    0 0:0:0:0           да 2600,0000 800,0000  979,1000
  1    0      0    0 0:0:0:0           да 2600,0000 800,0000  801,0970
  2    0      0    1 4:4:1:0           да 2600,0000 800,0000  898,6870
  3    0      0    1 4:4:1:0           да 2600,0000 800,0000  800,0000
  4    0      0    2 8:8:2:0           да 2600,0000 800,0000  800,0000
  5    0      0    2 8:8:2:0           да 2600,0000 800,0000  800,0000
  6    0      0    3 12:12:3:0         да 2600,0000 800,0000  900,0000
  7    0      0    3 12:12:3:0         да 2600,0000 800,0000  800,0000
  8    0      0    4 16:16:4:0         да 2600,0000 800,0000 1000,0000
  9    0      0    4 16:16:4:0         да 2600,0000 800,0000  800,0000
 10    0      0    5 20:20:5:0         да 2600,0000 800,0000  803,7280
 11    0      0    5 20:20:5:0         да 2600,0000 800,0000  800,0000
 12    0      0    6 24:24:6:0         да 1900,0000 800,0000  893,7550
 13    0      0    7 25:25:6:0         да 1900,0000 800,0000  900,1650
 14    0      0    8 26:26:6:0         да 1900,0000 800,0000  900,0920
 15    0      0    9 27:27:6:0         да 1900,0000 800,0000  848,8350
 16    0      0   10 28:28:7:0         да 1900,0000 800,0000  799,8250
 17    0      0   11 29:29:7:0         да 1900,0000 800,0000  799,7880
 18    0      0   12 30:30:7:0         да 1900,0000 800,0000  968,8110
 19    0      0   13 31:31:7:0         да 1900,0000 800,0000  799,5460
```

</details>

---

## 4. Кэш-память процессора

Команда:

```bash
cat /proc/cpuinfo | grep -i cache
```

<details>
<summary>Вывод команды</summary>

```text
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
cache size	: 24576 KB
cache_alignment	: 64
```

</details>

---

## 5. Оперативная память

Команда:

```bash
free -h
```

<details>
<summary>Вывод команды</summary>

```text
               total        used        free      shared  buff/cache   available
Память:         15Gi       6,4Gi       2,0Gi       1,4Gi       7,7Gi       9,0Gi
Подкачка:      4,0Gi       256Ki       4,0Gi
```

</details>

---

## 6. Информация о дисках и памяти

Команда:

```bash
sudo lshw -class disk -class memory -short
```

<details>
<summary>Вывод команды</summary>

```text
H/W path         Устройство  Класс     Описание
======================================================================
/0/0                                   memory         128KiB BIOS
/0/4/a                                 memory         512KiB L1 кэш
/0/4/b                                 memory         4MiB L2 кэш
/0/4/c                                 memory         24MiB L3 кэш
/0/5                                   memory         288KiB L1 кэш
/0/6                                   memory         192KiB L1 кэш
/0/7                                   memory         7680KiB L2 кэш
/0/8                                   memory         24MiB L3 кэш
/0/9                                   memory         256KiB L1 кэш
/0/22                                  memory         16GiB Системная �
/0/22/0                                memory         8GiB SO-DIMM Синхро�
/0/22/1                                memory         8GiB SO-DIMM Синхро�
/0/100/14.2                            memory         RAM memory
/0/100/1d/0/0    hwmon7                disk           NVMe disk
/0/100/1d/0/2    /dev/ng0n1            disk           NVMe disk
/0/100/1d/0/1    /dev/nvme0n1          disk           1024GB NVMe disk
```

</details>

---

## 7. SMART и тип накопителя

Сначала определить имя накопителя:

```bash
lsblk -d -o NAME,MODEL,SIZE,ROTA,TYPE
```

<details>
<summary>Вывод команды</summary>

```text
ВСТАВИТЬ ВЫВОД СЮДА
```

</details>

После этого выполнить команду для нужного устройства.

Например, для `/dev/sda`:

```bash
sudo smartctl -a /dev/sda
```

Или для NVMe:

```bash
sudo smartctl -a /dev/nvme0n1
```

<details>
<summary>Вывод SMART</summary>

```text
ВСТАВИТЬ ВЫВОД СЮДА
```

</details>

---

## 8. Вращающийся или невращающийся накопитель

Заменить `sdX` на имя устройства, например `sda` или `nvme0n1`.

```bash
cat /sys/block/sdX/queue/rotational
```

<details>
<summary>Вывод команды</summary>

```text
ВСТАВИТЬ ВЫВОД СЮДА
```

</details>

Интерпретация:

- `0` — невращающийся накопитель, обычно SSD/NVMe;
- `1` — вращающийся накопитель, HDD.

---

## 9. Число доступных логических CPU

Команда:

```bash
nproc
```

<details>
<summary>Вывод команды</summary>

```text
ВСТАВИТЬ ВЫВОД СЮДА
```

</details>

---

## 10. NUMA-топология

Команда:

```bash
numactl --hardware
```

<details>
<summary>Вывод команды</summary>

```text
ВСТАВИТЬ ВЫВОД СЮДА
```

</details>

---

## Дополнительно

Если необходимые утилиты отсутствуют:

```bash
sudo apt update
sudo apt install lshw smartmontools numactl
```
