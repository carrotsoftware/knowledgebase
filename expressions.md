# База знаний

!> TODO

## Автомасштабирование текста по фиксированной ширине

![Expression for Text Layer Scaling to Fixed Border](_images/expression_text-scale_border.gif)

Скопируйте это выражение в свойство **`Scale`** слоя **TextLayer**:

```
const targetLayer = thisComp.layer("TextLayer");
const borderWidth_px = 600;

let targetWidth = targetLayer.sourceRectAtTime().width;
let scaleValue = 60; // Изначальный масштаб слоя
let scaleCoef = (scaleValue-100) * .01;

let targetWidthScaled_px = targetWidth + (targetWidth * scaleCoef);
let targetWidthScaled_converted = scaleValue;

if (targetWidthScaled_px > borderWidth_px) {
		targetWidthScaled_converted = borderWidth_px / targetWidthScaled_px * scaleValue;
} else {targetWidthScaled_converted};

[targetWidthScaled_converted,targetWidthScaled_converted]
```