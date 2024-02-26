Этот тернистый путь 🌵 в мир магии 🌟 нейросетевых технологий не потребует много времени ⏳ — около 30 минут ⌛, зато к концу пути вы станете немного волшебниками 🧙‍♂️.

## Установка Pinokio 📦

Pinokio — это программа 🖥️, позволяющая автоматически устанавливать, запускать и программно управлять ЛЮБЫМИ приложениями 🔄. Она позволяет упростить процесс установки и управления разнообразными приложениями — за несколько шагов вы сможете начать использовать самые последние достижения искусственного интеллекта 🧠, не тратя время на сложные настройки и установки.

## Системные требования 💻

Перед началом установки убедитесь, что ваш компьютер соответствует следующим требованиям:

- Минимум 35 Гб свободного места на диске 💾
- Минимум 6 Гб видеопамяти 🎮

## Установка Pinokio 📲

### Шаг 1: Скачивание 📥

1. Переходим по ссылке [https://pinokio.computer/](https://pinokio.computer/)
2. Жмём **Download** и скачиваем установщик для своей ОС.

### Шаг 2: Установка 🔧

3. Запускаем установщик и следуем инструкциям на экране. Убедитесь, что на диске достаточно свободного места (не менее **35 Гб**).

![Установка Pinokio](https://i.imgur.com/72m9Bxa.png)

### Шаг 3: Поиск и установка приложений 🔍

4. После запуска приложения переходим по Discover Page и в поисковой строке набираем "automatic1111".

![Установка компонентов](https://i.imgur.com/MQ7Yd4w.png)

![Discover Page](https://i.imgur.com/YGwwmn4.png)

5. Нажимаем "Download" и соглашаемся со всей установкой "Install". Ждём завершения установки.

### Шаг 4: Запуск приложения 🚀

6. После установки запускаем лаунчер "Stable Diffusion web UI", нажимаем Install и ждём завершения установки.

![Stable Diffusion web UI](https://i.imgur.com/CxyvnoN.png)

7. Нажимаем **Start**

![](https://i.imgur.com/uDd42EG.png)

8. Ждём, когда в консоли появится сообщение "Model loaded".

![Консоль](https://i.imgur.com/6h5BZpm.png)

### Шаг 5: Использование 🖱️

9. Открываем свой браузер и переходим по адресу [http://127.0.0.1:7860/](http://127.0.0.1:7860/) для доступа к интерфейсу приложения.

![Интерфейс приложения](https://i.imgur.com/7mvUcVT.png)



# Руководство по использованию Automatic1111 с InstandID для Stable Diffusion

## Введение

Automatic1111 представляет собой пользовательский интерфейс для работы с нейросетью Stable Diffusion с помощью браузера, например, через `localhost` на [http://127.0.0.1:7860/](http://127.0.0.1:7860/). 

## Начало работы

### Генерация изображений из текста

1) Для начала генерации изображений используйте поле запроса `Prompt` с примером:

```
cartoon illustration of full body Barbie doll in pink dress, short blonde hairs, by Patrick Nagel,vector art,few colors,bright
```

2) Затем нажмите `Generate`, чтобы увидеть МАГИЮ

![Пример генерации](https://i.imgur.com/o65tGwO.png)

### Важные указания

**Для того чтобы все изображения гармонично сочетались в одном стиле важно использовать для всех изображений одни и те же настройки!**

В сети есть множество моделей Stable Diffusion, которые были дотренированы на дополнительных изображениях, которых не было в базовой версии нейросети. Я выбрал модель DreamShaper XL, она позволяет делать хорошие фотореалистичные изображения вымышленных персонажей (и не только). Я использую её модификацию v2.1 Turbo DPM++ SDE, которая позволяет существенно ускорить время генерации (за счёт несущественной потери качества и гибкости нейросети, что в нашем случае не критично, так как мы используем векторный стиль без высокой детализации). Внимание модель нецензурированная, на выходе может быть NSFW!

### Выбор и установка модели

3) Скачайте модель `DreamShaper XL v2.1 Turbo DPM++ SDE` с [civitai.com](https://civitai.com/models/112902/dreamshaper-xl).

![Скачивание модели](https://i.imgur.com/VK4BHR6.png)

4). Перенесите файл модели в папку с моделями нейросети, следуя пути `app/models/Stable-diffusion` в вашем локальном хранилище Automatic1111.

![Перенос модели](https://i.imgur.com/PkKi3RU.png)

### Настройка параметров генерации

5) В интерфейсе Automatic1111 выставите следующие параметры генерации:

- **Sampling steps:** `8`
- **CFG Scale:** `2`
- **Размеры изображения:** `1024x1024`
- **Seed:** `549212795` (или другое значение для разнообразия результатов)
- **Sampler:** `DPM++ SDE Karras` (важно для работы Turbo модели)

6) Для уменьшения вероятности получения NSFW-контента и картинок низкого качества, используйте следующий список исключений в поле негативного запроса:

```
NSFW, naked, nude, lowres, text, error, cropped, worst quality, low quality, jpeg artifacts, ugly, duplicate, morbid, mutilated, out of frame, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, mutation, deformed, blurry, dehydrated, bad anatomy, bad proportions, extra limbs, cloned face, disfigured, gross proportions, malformed limbs, missing arms, missing legs, extra arms, extra legs, fused fingers, too many fingers, long neck, username, watermark, signature
```

Это поможет уменьшить риск нежелательных результатов, но не гарантирует их полное отсутствие, *я предупредил*.

### Генерация и результаты

7) После настройки параметров нажмите `Generate` и ожидайте результата.

![Пример результата](https://i.imgur.com/uocqrf9.png)

### Установка ControlNet

Для генерации изображения человека по его фотографии, воспользуемся модулем нейросети ControlNet.

8) Переходим во вкладку **Extensions** > **Install From URL**.
9) Вставляем URL расширения:
```
https://github.com/Mikubill/sd-webui-controlnet
```
10) Нажимаем **Install**.

![Установка ControlNet](https://i.imgur.com/X6peBJ9.png)

11) После установки расширения переходим в субвкладку **Installed** и выбираем **Apply and Restart UI**.

![Применение изменений](https://i.imgur.com/hA0gcSR.png)

### Настройка ControlNet

12) После перезагрузки UI, во вкладке txt2img появится меню ControlNet.

![Меню ControlNet](https://i.imgur.com/dshwEEB.png)

13) Необходимо скачать и поместить модели в каталог `{A1111_root}/models/ControlNet`:

- [ipadapter model](https://huggingface.co/InstantX/InstantID/resolve/main/ip-adapter.bin?download=true)
- [ControlNet model](https://huggingface.co/InstantX/InstantID/resolve/main/ControlNetModel/diffusion_pytorch_model.safetensors?download=true)

14) Переименуйте скачанные файлы в `ip-adapter_instant_id_sdxl.bin` и `control_instant_id_sdxl.safetensors` для корректного распознавания расширением.

15) Обновите список моделей ControlNet ![Обновление списка моделей](https://i.imgur.com/aQYJtvy.png)

## Настройка ControlNet Units

### ControlNet Unit0

16) Раскройте меню **ControlNet Unit0**.
17) Выберите **ControlType InstantID**.
![Настройка Unit0](https://i.imgur.com/qkgV9QT.png)
18) Установите **instant_id_face_embedding** для препроцессора и **ip-adapter_instan_id_sdxl** для модели.
![](https://i.imgur.com/ZS0Pqrv.png)
19) Установите **Control Weight** на **0.8**.

### ControlNet Unit1

20) Аналогично, во вкладке **ControlNet Unit1** выберите **ControlType InstantID**.
21) На этот раз выберите **instant_id_face_keypoints** для препроцессора и **control_instant_id_sxdl** для модели.

![Настройка Unit1](https://i.imgur.com/VBmgH1k.png)

22) Установите **Control Weight** на **0.8**.

## Генерация изображения

23) В поле **SingleImage** вставьте фотографию человека. Например, для добавления фото Леры, перейдите на страницу [Bukova Valeriya Igorevna](https://ntcup.ru/nashi-dostizheniya/stc-ui-ras-researchers/bukova-valeriya-igorevna/), скопируйте изображение и вставьте в поле **SingleImage** для **ControlNet Unit 0** с помощью Ctrl+V. И также для **ControlNet Unit 1**
	- Убедитесь, что установлены галочки **Enable** и **Pixel Perfect**.
	- Пропорции генерируемого изображения и фотографии должны совпадать для оптимального результата (то есть для квадратных изображений лучше использовать квадратные фотографии).

Должно получиться подобное изображение

![Пример генерации](https://i.imgur.com/IVTHLLJ.png)

> cartoon illustration of full body Barbie doll in pink dress, short blonde hairs, by Patrick Nagel,vector art,few colors,bright
Negative prompt: NSFW, naked, nude, lowres, text, error, cropped, worst quality, low quality, jpeg artifacts, ugly, duplicate, morbid, mutilated, out of frame, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, mutation, deformed, blurry, dehydrated, bad anatomy, bad proportions, extra limbs, cloned face, disfigured, gross proportions, malformed limbs, missing arms, missing legs, extra arms, extra legs, fused fingers, too many fingers, long neck, username, watermark, signature
Steps: 8, Sampler: DPM++ SDE Karras, CFG scale: 2, Seed: 549212795, Size: 1024x1024, Model hash: 4496b36d48, Model: dreamshaperXL_v21TurboDPMSDE, Clip skip: 2, ControlNet 0: "Module: instant_id_face_embedding, Model: ip-adapter_instant_id_sdxl [eb2d3ec0], Weight: 0.8, Resize Mode: Crop and Resize, Low Vram: False, Processor Res: 512, Guidance Start: 0, Guidance End: 1, Pixel Perfect: True, Control Mode: Balanced, Hr Option: Both, Save Detected Map: True", ControlNet 1: "Module: instant_id_face_keypoints, Model: control_instant_id_sdxl [c5c25a50], Weight: 0.8, Resize Mode: Crop and Resize, Low Vram: False, Processor Res: 512, Guidance Start: 0, Guidance End: 1, Pixel Perfect: True, Control Mode: Balanced, Hr Option: Both, Save Detected Map: True", Version: v1.6.0-2-g4afaaf8a


## Массовая генерация изображений

Чтобы сгенерировать несколько изображений в различном стиле:

24) Откройте меню **Scripts**.
25) Выберите "X\Y\Z Plot".
26) Установите **"X Type"** как **Nothing**, **"Y Type"** как **"Prompt S / R"**, и в поле **"Y Values"** вставьте:

```
Barbie doll in pink dress, Superwoman with a cape flying with her fist forward showcasing her strength and heroism, Ellen Ripley from "Alien" series with her signature flame thrower, Mera from aquaman with a trident, Galadriel with a silver elven circlet, Jasmine from Disney with golden circle earrings and golden necklace, woman ghostbuster, Katniss Everdeen with arrows in black armor, Sarah Connor in bulletproof vest, Wonder Woman with a cape Lara Croft from "Tomb Raider" equipped with dual pistols, Xena Warrior Princess with her chakram and sword, Rey from the "Star Wars" sequel trilogy wielding a lightsaber, Sailor Moon from the anime series with her moon stick, Éowyn from "The Lord of the Rings" with her sword, Leeloo from "The Fifth Element" with her multi-pass and orange suspenders outfit, Princess Leia from "Star Wars" with her blaster and iconic white dress, Daenerys Targaryen from "Game of Thrones" with a dragon perched on her shoulder, Spider-Gwen from the Spider-Verse in her white and pink spider suit swinging on a web, Catwoman from the DC Universe in her sleek black leather suit holding a whip, Rapunzel from Disney "Tangled" with her long magical blonde hair, Ahsoka Tano from the "Star Wars" universe dual-wielding lightsabers, Merida from Disney "Brave" with her bow and arrow ready to shoot, Harley Quinn from the DC Universe wielding her signature mallet, Jean Grey as Phoenix from the X-Men surrounded by flames, Sakura Haruno from "Naruto" ready to unleash her medical ninjutsu
```

27) Дождитесь завершения генерации и откройте папку с изображениями, нажав на соответствующую иконку ![иконка](https://i.imgur.com/OFejT9Y.png)

## Обмен изображениями

После генерации изображений скидываем их на общий диск в соответствующую папку. Приглашения для доступа к папке я высылаю на рабочую почту:

[https://disk.yandex.ru/client/disk/Stable%20Difusion](https://disk.yandex.ru/client/disk/Stable%20Difusion)

## Дополнительная информация

- Более подробно о Stable Diffusion можно узнать [здесь](https://habr.com/ru/companies/skillfactory/articles/685508/).
- Подробная инструкция об InstantID доступна [здесь](https://github.com/Mikubill/sd-webui-controlnet/discussions/2589).
- Видеоинструкция на YouTube: [InstantID — генерация с вашим лицом](https://www.youtube.com/watch?v=x9B59v5V3zI).


## Поддержка и обратная связь

Если у вас возникли вопросы или нужна помощь в процессе установки и использования Pinokio и Stable Diffusion, обращайтесь ко мне в личные сообщения в Telegram: **LoFiLight**.
