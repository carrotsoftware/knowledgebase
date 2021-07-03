# База знаний

В этом разделе представлены часто используемые выражения при подготовке шаблонов для **Carrot Engine** в **Adobe After Effects**.

## Автомасштабирование текста по фиксированной ширине
![Expression for Text Layer Scaling to Fixed Border](_images/expression_text-scale_border.gif)

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
var targetLayer = thisComp.layer("TextLayer");
var borderWidth = 600; // Ширина границы в пикселях

var targetWidth = targetLayer.sourceRectAtTime().width;
var scaleValue = 60; // Изначальный масштаб target слоя
var scaleCoef = (scaleValue - 100) * .01;

var targetWidthScaled_px = targetWidth + (targetWidth * scaleCoef);
var targetWidthScaled_converted = scaleValue;

if (targetWidthScaled_px > borderWidth) {
		targetWidthScaled_converted = borderWidth / targetWidthScaled_px * scaleValue;
} else {targetWidthScaled_converted};

[targetWidthScaled_converted,targetWidthScaled_converted]
```

## Динамическая плашка под размер текста из солида
![Expression for Solid Layer Scaling to Text Size](_images/expression_solid-scale_text.gif)

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
var targetLayer = thisComp.layer("TextLayer");
var scaleValue = 60; // Изначальный масштаб target слоя

var solidLayer = thisComp.layer("SolidPlate");
var hBorder = 100; // Размер границы по горизонтали
var vBorder = 25; // Размер границы по вертикали

var targetWidth = targetLayer.sourceRectAtTime().width;
var targetHeight = targetLayer.sourceRectAtTime().height;
var scaleCoef = (scaleValue - 100) * .01;

var solidWidth = solidLayer.sourceRectAtTime().width;
var solidHeight = solidLayer.sourceRectAtTime().height;

if (targetWidth == 0) {hBorder = 0, vBorder = 0};

var targetWidthScaled_px = targetWidth + (targetWidth * scaleCoef);
var targetHeightScaled_px = targetHeight + (targetHeight * scaleCoef);

var targetWidthScaled_converted = (targetWidthScaled_px + hBorder) / solidWidth * 100;
var targetHeightScaled_converted = (targetHeightScaled_px + vBorder) / solidHeight * 100;

[targetWidthScaled_converted,targetHeightScaled_converted]
```
> **Важно:** Для работы этого шаблона свойство **`Anchor Point`** у **SolidPlate** должно совпадать с выравниванием текста.
>
>**Например:** Если выравнивание текста выставлено по левому краю, то **`Anchor Point`** у **SolidPlate** должен находиться в левом углу слоя.

> **Примечание:** Вспомогательные переменные в выражениях можно привязать к значениям **элементов управления выражений** **(Expression Controls)**. 
>
> Эти элементы управления можно вывести в **Carrot Template Preview** в качестве новой переменной и редактировать её через **Carrot Web Playlist** без необходимости реэкспорта шаблона.