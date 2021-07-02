# База знаний

В этом разделе представлены часто используемые выражения при подготовке шаблонов для **Carrot Engine** в **Adobe After Effects**.

## Автомасштабирование текста по фиксированной ширине
![Expression for Text Layer Scaling to Fixed Border](_images/expression_text-scale_border.gif)

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
const targetLayer = thisComp.layer("TextLayer");
const borderWidth = 600; // Ширина границы в пикселях

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

## Динамическая плашка под ширину текста из солида
!> TODO

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
var targetLayer = thisComp.layer("TextLayer");
var scaleValue = 60; // Изначальный масштаб target слоя
var solidLayer = thisComp.layer("SolidPlate");
var hBorder = 50; // Размер границы по горизонтали

var targetWidth = targetLayer.sourceRectAtTime().width;
var scaleCoef = (scaleValue - 100) * .01;
var solidWidth = solidLayer.sourceRectAtTime().width;

if (targetWidth == 0) {hBorder = 0};

var targetWidthScaled_px = targetWidth + (targetWidth * scaleCoef);
var targetWidthScaled_converted = (targetWidthScaled_px + hBorder) / solidWidth * 100;

[targetWidthScaled_converted,100]
```
Скопируйте это выражение в свойство **`Position`** слоя **TextLayer**:

```javascript
!> TODO
```
> **Примечание:** Вспомогательные переменные в выражениях можно привязать к значениям **элементов управления выражений** **(Expression Controls)**. 
>
> Эти элементы управления можно вывести в **Carrot Template Preview** в качестве новой переменной и редактировать её через **Carrot Web Playlist** без необходимости реэкспорта шаблона.