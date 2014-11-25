# Технические требования SDK Adcamp к HTML5/Mraid баннерам

### Изолированная среда для креатива
В целях безопасности площадки рекламодателя, в Web SDK запрещается обращение к родительского странице из созданного iframe.

**Неправильно:**
```
window.parent.document.body.append(script);
```

Также iframe накладывает ограничения, не свойственные корневому окну, поэтому необходимо удостовериться в корректной работе креатива из third-party фрейма.
* * *

### Destination link
Для корректного взаимодействия с системой статистики, все ссылки на целевое действие должны быть отмечены классом "adc_clickarea".

**Неправильно:**
```
<a href="http://example.com" target="_blank">Target</a>
<div onclick="mraid.open('http://example.com')">Target</div>
```
**Правильно:**
```
// К этому элементу будет добавлен линк с нашим баунсером
<div class="adc_clickarea">Target</div>
```
* * *
### Создание креатива
mraid.open() не должен вызываться при инициализации, иначе загрузчик выбросит исключение.
* * *
### Resize
Для изменения размера креатива необходимо назначить новые параметры для ресайза и выполнить метод mraid.resize()

**Пример:**
```
  var screenSize = mraid.getScreenSize(); 
  var resizeProperties = { 
    "width": screenSize.width, 
    "height": screenSize.height/2, 
    "offsetX": 0,
    "offsetY": screenSize.height/10, 
    "allowOffscreen": false 
  }
mraid.setResizeProperties(resizeProperties);
mraid.resize(); 
```
* * *
### Закрытие рекламы
Уничтожение рекламы должно происходить только с помощью mraid.close(), в противном случае после закрытия баннера останется обертка.
* * *
### Методы для работы с mraid в Web SDK

Методы копируют поведение mraid.js для приложений. [Спецификация MRAID](http://www.iab.net/media/file/IAB_MRAID_v2_FINAL.pdf)
#### mraid.getState()
Возвращает текущее состояние баннера (string)
Возвращаемые значения: loading (default), default, expanded, resized, hidden

#### mraid.getPlacementType()
Возвращает тип плейсмента (string)
Возвращаемые значения: inline, interstitial

#### mraid.getScreenSize()
Возвращает объект с размерами экрана (object)
{width: (int), height: (int)}

#### mraid.getCurrentPosition()
Возвращает объект с размерами креатива и его отступами по осям (object)
{x: (int), y: (int), width: (int), height: (int)}

#### mraid.getExpandProperties()
Возвращает объект с настройками expand состояния (object)
{width: (int), height: (int), useCustomClose: (bool), isModal: (bool)}

#### mraid.isViewable()
Возвращает видимость объекта (bool)

#### mraid.getOrientationProperties()
Возвращает объект с параметрами смены ориентации объекта (bool)

#### mraid.setOrientationProperties(allowOrientationChange(bool), forceOrientation (str))
Возвращает объект с параметрами смены ориентации объекта (bool)

#### mraid.addEventListener(event, handler)
Назначает слушатель на событие

#### mraid.removeEventListener(event)
Уничтожает слушателя событие

#### mraid.expand()
Разворачивает фрейм на весь экран

#### mraid.close()
Если состояние expanded - возвращает в default, иначе - аналогичен mraid.destroy()

#### mraid.destroy()
Уничтожает фрейм
