# Fastfetch Custom Logo Guide (Termux)

🌐 [English](#english-version) | [Русский](#русская-версия)

---

## English Version

A step-by-step guide to setting up a custom text-based logo in Fastfetch inside the Termux emulator.

> [!WARNING]
> This guide is verified to work on **Fastfetch version 2.63**. In newer versions (including 2.65), the configuration structure has changed, and this setup may not function correctly.
> 
> **How to compile the working version from source using Ninja:**
> ```bash
> pkg update && pkg upgrade -y
> pkg install git cmake clang python ninja binutils -y
> git clone https://github.com/fastfetch-cli/fastfetch.git
> cd fastfetch && git checkout 2.63.0
> mkdir -p build && cd build
> cmake .. -G Ninja -DCMAKE_BUILD_TYPE=Release
> ninja && ninja install
> ```

---

### 🛠️ Step 1. Install Chafa
Install the image-to-character converter:
```bash
pkg install chafa
```

### 🖼️ Step 2. Convert Your Image to Text
Create a text file containing the logo from your image (replace `/sdcard/logo.jpeg` with the actual path to your image):
```bash
chafa /sdcard/logo.jpeg --size 26x13 > ~/logo.txt
```

### ⚙️ Step 3. Generate Fastfetch Configuration
Generate the default configuration file if you haven't already:
```bash
fastfetch --gen-config
```

### 📝 Step 4. Edit the Configuration File
Open the configuration file using the Nano text editor:
```bash
nano ~/.config/fastfetch/config.jsonc
```

### 🧩 Step 5. Configure the Logo Block
Find the `"logo"` block and replace it with the code below. If it does not exist, insert this code right after the first opening curly bracket `{`. Make sure there is a comma after the closing bracket of the logo block:
```json
  "logo": {
      "type": "raw",
      "source": "/data/data/com.termux/files/home/logo.txt",
      "width": 26,
      "height": 13
  },
```

> [!NOTE]
> The height is set to `13` to match the conversion size used in Step 2.

### 💾 Step 6. Save and Exit
* Press `Ctrl + O`, then hit `Enter` to save.
* Press `Ctrl + X` to exit.

---

## Русская версия

Инструкция по установке кастомного текстового логотипа в утилиту Fastfetch внутри эмулятора Termux.

> [!WARNING]
> Данное руководство гарантированно работает на версии **Fastfetch 2.63**. На более новых версиях (включая 2.65) структура параметров изменилась, и текущая конфигурация может работать некорректно.
> 
> **Как скомпилировать рабочую версию из исходников через Ninja:**
> ```bash
> pkg update && pkg upgrade -y
> pkg install git cmake clang python ninja binutils -y
> git clone https://github.com/fastfetch-cli/fastfetch.git
> cd fastfetch && git checkout 2.63.0
> mkdir -p build && cd build
> cmake .. -G Ninja -DCMAKE_BUILD_TYPE=Release
> ninja && ninja install
> ```

---

### 🛠️ Шаг 1. Установка утилиты Chafa
Установите конвертер изображений в текстовые символы:
```bash
pkg install chafa
```

### 🖼️ Шаг 2. Конвертация изображения в текст
Создайте текстовый файл с логотипом из вашей картинки (замените `/sdcard/logo.jpeg` на свой путь к изображению):
```bash
chafa /sdcard/logo.jpeg --size 26x13 > ~/logo.txt
```

### ⚙️ Шаг 3. Создание конфигурации Fastfetch
Сгенерируйте стандартный файл настроек, если вы еще этого не делали:
```bash
fastfetch --gen-config
```

### 📝 Шаг 4. Редактирование конфигурации
Откройте файл настроек через текстовый редактор Nano:
```bash
nano ~/.config/fastfetch/config.jsonc
```

### 🧩 Шаг 5. Настройка блока Logo
Найдите блок `"logo"` и замените его код представленным ниже. Если блок отсутствует, вставьте этот код сразу после первой открывающей фигурной скобки `{`. Убедитесь, что после закрывающей скобки блока стоит запятая:
```json
  "logo": {
      "type": "raw",
      "source": "/data/data/com.termux/files/home/logo.txt",
      "width": 26,
      "height": 13
  },
```

> [!NOTE]
> Высота установлена на `13` в соответствии с размером конвертации из Шага 2.

### 💾 Шаг 6. Сохранение файла
* Нажмите `Ctrl + O`, затем `Enter` для сохранения изменений в Nano.
* Нажмите `Ctrl + X` для выхода из редактора.
