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
ms.openlocfilehash: 449fb0c12b11163ba0ceca981e66a7da0c399e1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950203"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Класс BoundsRules ограничивает расположение и размеры фигур

Объект *правило границ* — это класс, который определяет ограничения на размер и расположение фигуры. Он предоставляет метод, который вызывается многократно при перетаскивании пользователем фигуры или углы или границы фигуры.

Следующий пример ограничивает прямоугольную форму, чтобы быть фиксированного размера, горизонтальной или вертикальной чертой. Когда пользователь перетаскивает углы или сторон, контура переворачивается между две конфигурации разрешенных высоты и ширины.

Привязывает правило, является класс, производный от <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Экземпляр правила создается в фигуре.

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

Обратите внимание на то, что если вы хотите, чтобы может быть ограничена расположение и размер.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Обработка и распространение изменений](../modeling/responding-to-and-propagating-changes.md)