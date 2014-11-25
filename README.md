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
Для корректного взаимодействия с системой статистики, все ссылки на целевое действие должны быть отмечены классом "clickarea".

**Неправильно:**
```
<a href="http://example.com" target="_blank">Target</a>
<a onclick="mraid.open('http://example.com')" target="_blank">Target</a>
```
**Правильно:**
```
// К этому элементу будет добавлен линк с нашим баунсером
<a class="clickarea" target="_blank">Target</a>
```
* * *


# Методы для работы с mraid в Web SDK

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
