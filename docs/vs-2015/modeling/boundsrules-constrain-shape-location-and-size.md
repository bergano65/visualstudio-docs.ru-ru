---
title: Баундсрулес ограничить расположение и размер фигуры | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672731"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Класс BoundsRules ограничивает расположение и размеры фигур
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Правило границ* — это класс, определяющий ограничения на размер и расположение фигуры. Он предоставляет метод, который вызывается многократно, пока пользователь перетаскивает фигуру или углы или стороны фигуры.

 В следующем примере прямоугольная фигура ограничивается полосой фиксированного размера, горизонтальной или вертикальной. Когда пользователь перетаскивает углы или стороны, контур переворачивается между двумя разрешенными настройками высоты и ширины.

 Правило Bounds является классом, производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Экземпляр правила создается в фигуре:

```
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

 Обратите внимание, что при необходимости расположение и размер могут быть ограничены.

## <a name="see-also"></a>См. также раздел
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [реагирования на изменения и распространения изменений](../modeling/responding-to-and-propagating-changes.md)
