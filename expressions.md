# База знаний

В этом разделе представлены часто используемые выражения при подготовке шаблонов для **Carrot Engine** в **Adobe After Effects**.

## Автомасштабирование текста по фиксированной ширине
![Expression for Text Layer Scaling to Fixed Border](_images/expression_text-scale_border.gif)

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
const targetLayer = thisComp.layer("TextLayer");
const borderWidth = 600; // Ширина границы в пикселях

var targetWidth = targetLayer.sourceRectAtTime().width;
var scaleValue = 60; // Изначальный масштаб слоя
var scaleCoef = (scaleValue - 100) * .01;

var targetWidthScaled_px = targetWidth + (targetWidth * scaleCoef);
var targetWidthScaled_converted = scaleValue;

if (targetWidthScaled_px > borderWidth) {
		targetWidthScaled_converted = borderWidth / targetWidthScaled_px * scaleValue;
} else {targetWidthScaled_converted};

[targetWidthScaled_converted,targetWidthScaled_converted]
```

## Выравнивание и масштабирование солида под конкретный слой
!> TODO

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
H_Padding = 100;
W_Padding = 100;
 
var Target = thisComp.layer("Text").sourceRectAtTime();
 
H = Target.height;
W = Target.width;
 
[W+W_Padding,H+H_Padding]
```
Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
H_Spacing = 50;
W_Spacing = 0;
 
var Target = thisComp.layer("Text").sourceRectAtTime();
 
H = Target.height;
W = Target.width;
 
thisComp.layer("Text").transform.position+[W_Spacing,Target.top-H_Spacing]
```
> **Примечание:** Вспомогательные переменные в выражениях можно привязать к значениям **элементов управления выражений** **(Expression Controls)**. 
>
> Эти элементы управления можно вывести в **Carrot Template Preview** в качестве новой переменной и редактировать её через **Carrot Web Playlist** без необходимости реэкспорта шаблона.