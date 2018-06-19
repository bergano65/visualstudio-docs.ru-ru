---
title: Класс BoundsRules ограничивает расположение и размеры фигур
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 104a74a38099286675a742ce9eea367d9eeabe84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944392"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Класс BoundsRules ограничивает расположение и размеры фигур

Объект *правило границы* — это класс, который определяет ограничения на размер и расположение фигуры. Он предоставляет метод, который вызывается многократно, пока пользователь перетаскивает фигуры или углы или границы фигуры.

Следующий пример ограничивает прямоугольную форму, чтобы быть фиксированного размера, горизонтальной или вертикальной чертой. При перетаскивании углы или стороны контура зеркальное отражение между две конфигурации разрешенных высоты и ширины.

Границы правила является класс, производный от <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Экземпляр правила создается в той форме:

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

Обратите внимание, что если требуется, можно задать ограничения расположение и размер.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Обработка и распространение изменений](../modeling/responding-to-and-propagating-changes.md)