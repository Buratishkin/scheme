# Паспорт системы

Дата сбора: `ДД.ММ.ГГГГ`

> В этот файл нужно вставить вывод команд, характеризующих аппаратную и программную конфигурацию системы.
> Для длинного вывода используются сворачиваемые блоки `<details>`.

---

## 1. Ядро и архитектура

Команда:

```bash
uname -a
```

<details>
<summary>Вывод команды</summary>

```text
ВСТАВИТЬ ВЫВОД СЮДА
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
ВСТАВИТЬ ВЫВОД СЮДА
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
ВСТАВИТЬ ВЫВОД СЮДА
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
ВСТАВИТЬ ВЫВОД СЮДА
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
ВСТАВИТЬ ВЫВОД СЮДА
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
ВСТАВИТЬ ВЫВОД СЮДА
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
