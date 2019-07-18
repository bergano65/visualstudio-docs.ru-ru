---
title: Класс BoundsRules ограничивает расположение и размеры | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09be82be084767bfb2d300a1877e95456a957b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159668"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Класс BoundsRules ограничивает расположение и размеры фигур
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Объект *правило границ* — это класс, который определяет ограничения на размер и расположение фигуры. Он предоставляет метод, который вызывается многократно при перетаскивании пользователем фигуры или углы или границы фигуры.  
  
 Следующий пример ограничивает прямоугольную форму, чтобы быть фиксированного размера, горизонтальной или вертикальной чертой. Когда пользователь перетаскивает углы или сторон, контура переворачивается между две конфигурации разрешенных высоты и ширины.  
  
 Привязывает правило, является класс, производный от <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Экземпляр правила создается в фигуре.  
  
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
  
 Обратите внимание на то, что если вы хотите, чтобы может быть ограничена расположение и размер.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)
