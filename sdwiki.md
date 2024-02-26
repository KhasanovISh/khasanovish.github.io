Этот тернистый путь в мир магии нейросетей не потребует много времени — около 30 минут, зато к концу пути вы станете немного волшебниками. Все вопросы можно задавать мне в личные сообщения в Telegram LoFiLight

## Установка Pinokio

Pinokio — это программа, позволяющая автоматически устанавливать, запускать и программно управлять ЛЮБЫМИ приложениями. В том числе она позволяет максимально упростить процесс установки нейросетевых приложений.


1) Переходим по ссылке https://pinokio.computer/
2) Жмём Download и скачивем установщик для своей ОС
3) Запускаем установщик и приложение. На диске должно быть достаточно свободного места (не менее **35 Гб**)

![](https://i.imgur.com/72m9Bxa.png)

![](https://i.imgur.com/MQ7Yd4w.png)


4) Переходим по Discover Page и в поисковой строке набираем "automatic1111"
![](https://i.imgur.com/YGwwmn4.png)

5) Нажимаем "Download" и соглашаемся со всей установкой "Install". Ждём...
    - Все необходимые программные компоненты (Python, Visual studio и т.д.) устанавливаются во внутреннюю файловую систему Pinokio и не засоряют систему.
6) После установки запускаем лаунчер "Stable Diffusion web UI" и там тоже жмём Install и снова ждём
![](https://i.imgur.com/CxyvnoN.png)



7) Нажимаем Start ![](https://i.imgur.com/uDd42EG.png) снова открывается консоль ждём когда появится строчка "Model loaded"


![](https://i.imgur.com/6h5BZpm.png)


8) Открываем свой бразуер (Chrome, Firefox и т.д.) по адресу [http://127.0.0.1:7860/](http://127.0.0.1:7860/)

![](https://i.imgur.com/7mvUcVT.png)


## Automatic1111

Это интерефейс для работы с нейросетью Stable Diffusion через браузер, например через localhost [http://127.0.0.1:7860/](http://127.0.0.1:7860/)

1) Для генерации изображений из текста используется поле запроса Promt 

```
cartoon illustration of full body Barbie doll in pink dress, short blonde hairs, by Patrick Nagel,vector art,few colors,bright
```

остальное пока по умолчанию, проверяем работоспособность, жмём Generate и наблюдаем МАГИЮ
![](https://i.imgur.com/o65tGwO.png)


2) **Для того чтобы все изображения гармонично сочетались в одном стиле важно использовать для всех изображений одни и те же настройки!**

В сети есть множество моделей Stable Diffusion, которые были дотренированы на дополнительных изображениях, которых не было в базовой версии нейросети. Я выбрал модель DreamShaper XL, она позволяет делать хорошие фотореалистичные изображения вымышленных персонажей (и не только). Я использую её модификацию v2.1 Turbo DPM++ SDE, которая позволяет существенно ускорить время генерации (за счёт несущественной потери качества и гибкости нейросети, что в нашем случае не критично, так как мы используем векторный стиль без высокой детализации). Внимание модель нецензурированная, на выходе может выдаваться NSFW! 

Скачиваем эту модицификацию модели DreamShaper XL v2.1 Turbo DPM++ SDE на сайте [https://civitai.com/models/112902/dreamshaper-xl](https://civitai.com/models/112902/dreamshaper-xl)
![](https://i.imgur.com/VK4BHR6.png)


2) Переносим её в папку с моделями нейросети. Для это в pinokio переходим во вкладке Files по пути начиная от папки "app" в папку "models\Stable-diffusion". 

![](https://i.imgur.com/PkKi3RU.png)

Нажимаем View folder. Переносим скаченный файл `dreamshaperXL_v21TurboDPMSDE.safetensors` в эту папку, по умолчанию там также расположен файл `sd_xl_base_1.0.safetensors`
![](https://i.imgur.com/MHv5Ni9.png)


3) Обновляем список нейросетей в браузере

![](https://i.imgur.com/weN7XFP.png)


4) Далее выставляем параметры генерации:
    - Sampling steps: **8**
    - CFG Scale: **2**
    - Размеры изображения: **1024x1024**
    - Seed: например **549212795** (от него зависит генератор случайных чисел, изменяя его можно получать новые изображения, если получились неудачные, по умолчанию -1 автоматически выбирается случайное значение)
    - Sampler: **DPM++ SDE Karras** — это важно, с другими семплерами данная Turbo модель работать не будет.

в поле негативного запроса вставляем:

```
NSFW, naked, nude, lowres, text, error, cropped, worst quality, low quality, jpeg artifacts, ugly, duplicate, morbid, mutilated, out of frame, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, mutation, deformed, blurry, dehydrated, bad anatomy, bad proportions, extra limbs, cloned face, disfigured, gross proportions, malformed limbs, missing arms, missing legs, extra arms, extra legs, fused fingers, too many fingers, long neck, username, watermark, signature
```
это немного помогает от NSFW и плохих картинок, но 100% гарантии, что будет работать для всех изображений нет, *я предупредил*.


5) Запускаем Generate. Ждём магию, что оно всё работает.
![](https://i.imgur.com/uocqrf9.png)

6) Далее для генерации изображения человека на фото нужно использовать дополнительный модуль нейросети ControlNet. Для этого переходим во вкладку Extension и в её субвкладку Install From URL и вставляем URL:
```
https://github.com/Mikubill/sd-webui-controlnet 
```
нажимаем Install
![](https://i.imgur.com/X6peBJ9.png)

после того как расширение установилось переходим во субвкладку Installed и жмём Apply and Restart UI
![](https://i.imgur.com/hA0gcSR.png)


7) Теперь во вкладке txt2img должно появиться меню ControlNet
![](https://i.imgur.com/dshwEEB.png)

Вам необходимо скачать следующие модели и поместить их в каталог {A1111_root}/models/ControlNet тем же способом, что добавляли модель ранее:

- [ipadapter model](https://huggingface.co/InstantX/InstantID/resolve/main/ip-adapter.bin?download=true)
- [ControlNet model](https://huggingface.co/InstantX/InstantID/resolve/main/ControlNetModel/diffusion_pytorch_model.safetensors?download=true)

Также необходимо переименовать эти модели в `ip-adapter_instant_id_sdxl.bin` и `control_instant_id_sdxl.safetensors`, чтобы они корректно распознавались расширением!

и обновляем список моделей ControlNet![](https://i.imgur.com/aQYJtvy.png)



8) Раскрываем меню и в первой вкладке ControlNet Unit0 выбираем ControlType InstantID. 
![](https://i.imgur.com/qkgV9QT.png)

и далее instant_id_face_embedding для препоцессора и для модели ip-adapter_instan_id_sdxl (это важно)
![](https://i.imgur.com/ZS0Pqrv.png)

Control Weight устанавливаем на **0.8** 

9) Во второй вкладке ControlNet Unit1 также выбираем ControlType InstantID, но другой препроцессор `instant_id_face_keypoints` и модель `control_instant_id_sxdl`
![](https://i.imgur.com/VBmgH1k.png)

Control Weight устанавливаем на **0.8** 


10) В поле изображений SingleImage вставляем фотографию человека, например Миланы  в новой вкладке открываем https://ntcup.ru/nashi-dostizheniya/stc-ui-ras-researchers/bukova-valeriya-igorevna/ нажимаем "копировать изображение" (в Google Chrome) и возвращаемся во вкладку c Automatic1111, переносим курсор в поле фото SingleImage для ControlNet Unit 0 и нажимаем Ctrl+V.
     - Проверяем что установлены галочки **Enable** и **Pixel Perfect**
     - для квадратных изображений (ширина равна высоте) желательно брать также квадратные фото

11) Тоже самое проделываем для ControlNet Unit1

12) Ещё раз проверяем с помощью Generate

Должно получиться подобное изображение
![](https://i.imgur.com/IVTHLLJ.png)

> cartoon illustration of full body Barbie doll in pink dress, short blonde hairs, by Patrick Nagel,vector art,few colors,bright
Negative prompt: NSFW, naked, nude, lowres, text, error, cropped, worst quality, low quality, jpeg artifacts, ugly, duplicate, morbid, mutilated, out of frame, extra fingers, mutated hands, poorly drawn hands, poorly drawn face, mutation, deformed, blurry, dehydrated, bad anatomy, bad proportions, extra limbs, cloned face, disfigured, gross proportions, malformed limbs, missing arms, missing legs, extra arms, extra legs, fused fingers, too many fingers, long neck, username, watermark, signature
Steps: 8, Sampler: DPM++ SDE Karras, CFG scale: 2, Seed: 549212795, Size: 1024x1024, Model hash: 4496b36d48, Model: dreamshaperXL_v21TurboDPMSDE, Clip skip: 2, ControlNet 0: "Module: instant_id_face_embedding, Model: ip-adapter_instant_id_sdxl [eb2d3ec0], Weight: 0.8, Resize Mode: Crop and Resize, Low Vram: False, Processor Res: 512, Guidance Start: 0, Guidance End: 1, Pixel Perfect: True, Control Mode: Balanced, Hr Option: Both, Save Detected Map: True", ControlNet 1: "Module: instant_id_face_keypoints, Model: control_instant_id_sdxl [c5c25a50], Weight: 0.8, Resize Mode: Crop and Resize, Low Vram: False, Processor Res: 512, Guidance Start: 0, Guidance End: 1, Pixel Perfect: True, Control Mode: Balanced, Hr Option: Both, Save Detected Map: True", Version: v1.6.0-2-g4afaaf8a



13) Для того чтобы генировать много изображений, открываем меню Scripts в самом внизу, выбираем "X\Y\Z Plot" и для поля "X Type" выбираем Nothing для "Y Type" выбираем "Promt S / R" и в поле "Y Values" вставляем 
```
Barbie doll in pink dress, Superwoman with a cape flying with her fist forward showcasing her strength and heroism, Ellen Ripley from "Alien" series with her signature flame thrower, Mera from aquaman with a trident, Galadriel with a silver elven circlet, Jasmine from Disney with golden circle earrings and golden necklace, woman ghostbuster, Katniss Everdeen with arrows in black armor, Sarah Connor in bulletproof vest, Wonder Woman with a cape Lara Croft from "Tomb Raider" equipped with dual pistols, Xena Warrior Princess with her chakram and sword, Rey from the "Star Wars" sequel trilogy wielding a lightsaber, Sailor Moon from the anime series with her moon stick, Éowyn from "The Lord of the Rings" with her sword, Leeloo from "The Fifth Element" with her multi-pass and orange suspenders outfit, Princess Leia from "Star Wars" with her blaster and iconic white dress, Daenerys Targaryen from "Game of Thrones" with a dragon perched on her shoulder, Spider-Gwen from the Spider-Verse in her white and pink spider suit swinging on a web, Catwoman from the DC Universe in her sleek black leather suit holding a whip, Rapunzel from Disney "Tangled" with her long magical blonde hair, Ahsoka Tano from the "Star Wars" universe dual-wielding lightsabers, Merida from Disney "Brave" with her bow and arrow ready to shoot, Harley Quinn from the DC Universe wielding her signature mallet, Jean Grey as Phoenix from the X-Men surrounded by flames, Sakura Haruno from "Naruto" ready to unleash her medical ninjutsu
```
этот скрипт модифирует запрос к нейросети, заменяя строку до первой запятой последующами строками, разделенными запятыми

14) Ждём и открываем папку с изображениями нажав на иконку папки под кнопкой Generate.
![](https://i.imgur.com/OFejT9Y.png)



15) Скидываем их на общий диск в соответствующую папку. Приглашения для доступа к папке я высылаю на рабочую почту:
https://disk.yandex.ru/client/disk/Stable%20Difusion



## Дополнительная информация

- в общем о [Stable Diffusion — важнейшая нейросеть за всю историю генеративного искусства / Хабр](https://habr.com/ru/companies/skillfactory/articles/685508/)

Более подробно об InstantID написано здесь в инструкции https://github.com/Mikubill/sd-webui-controlnet/discussions/2589 
 - Видеоинструкция на YouTube [InstantID — генерация с вашим лицом. Полное руководство Huggingface, Colab, Portable, Automatic 1111](https://www.youtube.com/watch?v=x9B59v5V3zI)
