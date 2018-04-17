---
title: BoundsRules ограничивает расположение и размеры | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2474040edc439aad8a9dd75826d4918e6773e186
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Класс BoundsRules ограничивает расположение и размеры фигур
Объект *правило границы* — это класс, который определяет ограничения на размер и расположение фигуры. Он предоставляет метод, который вызывается многократно, пока пользователь перетаскивает фигуры или углы или границы фигуры.  
  
 Следующий пример ограничивает прямоугольную форму, чтобы быть фиксированного размера, горизонтальной или вертикальной чертой. При перетаскивании углы или стороны контура зеркальное отражение между две конфигурации разрешенных высоты и ширины.  
  
 Границы правила является класс, производный от <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Экземпляр правила создается в той форме:  
  
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
  
 Обратите внимание, что если требуется, можно задать ограничения расположение и размер.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)