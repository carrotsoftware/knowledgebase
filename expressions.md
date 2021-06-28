# База знаний

В этом разделе представлены часто используемые выражения при подготовке шаблонов для **Carrot Engine** в **Adobe After Effects**.

> **Примечание:** Вспомогательные переменные в выражениях можно привязать к значениям **элементов управления выражений** **(Expression Controls)**. 
>
> Эти элементы управления можно вывести в **Carrot Template Preview** в качестве новой переменной и редактировать её через **Carrot Web Playlist** без необходимости реэкспорта шаблона.

## Автомасштабирование текста по фиксированной ширине
![Expression for Text Layer Scaling to Fixed Border](_images/expression_text-scale_border.gif)

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```javascript
const targetLayer = thisComp.layer("TextLayer");
const borderWidth_px = 600;

let targetWidth = targetLayer.sourceRectAtTime().width;
let scaleValue = 60; // Изначальный масштаб слоя
let scaleCoef = (scaleValue - 100) * .01;

let targetWidthScaled_px = targetWidth + (targetWidth * scaleCoef);
let targetWidthScaled_converted = scaleValue;

if (targetWidthScaled_px > borderWidth_px) {
		targetWidthScaled_converted = borderWidth_px / targetWidthScaled_px * scaleValue;
} else {targetWidthScaled_converted};

[targetWidthScaled_converted,targetWidthScaled_converted]
```

## Автомасштабирование и выравнивание солида под конкретный слой
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
