# Интеграция SDK AdCamp в WEB

### Подготовка к работe
SDK AdCamp для мобильных WEB-страниц позволяет разработчикам размещать статичные и интерактивные рекламные объявления на своем сайте. Для начала необходимо подключить скрипт ротатации. 

**Пример:**
```
<!-- Подключаем ротатор -->
<script src="http://ssp3.adcamp.ru/loader.js" type="text/javascript">
```
* * *
### Теги с указаниями
Теперь сайт может взаимодействовать с рекламными серверами AdCamp. Для того, чтобы разместить объявление, в коде страницы необходимо создать рекламный блок с параметрами:
- pid – уникальный идентификатор вашего рекламного блока (генерируется нашей системой);
- width – ширина контейнера, в котором появится объявление;
- height – высота контейнера, в котором появится объявление.

**Пример:**
```
<!-- Подключаем рекламный блок -->
<div class="adc_block" 
	data-pid="5"
	data-width="320" 
	data-height="50" 
></div>
```
Размеры контейнера необходимы только для _стандартных_ и _плавающих_ блоков, в случае с _полноэкранными_ объявлениями они не нужны. 
* * *
### Поддерживаемые браузеры

- Safari (iOS 5.0+)
- Google Chrome
- Opera Coast
- Firefox
- Яндекс.Браузер
- Android browser (Android 2.3+)
- Internet Explorer (Windows Phone 7.0+)
- Nokia browser (Symbian 60S)
- OSS Browser (Symbian 60S)




