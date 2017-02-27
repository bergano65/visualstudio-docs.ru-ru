---
title: "Класс BoundsRules ограничивает расположение и размеры фигур | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Доменный язык, события"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# Класс BoundsRules ограничивает расположение и размеры фигур
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A *Bounds Rule* класс, который определяет ограничения на размер и расположение фигуры.  Он предоставляет метод, который вызывается повторно, пока пользователь перетаскивает фигуры или углы или края фигуры.  
  
 В следующем примере ограничиваются прямоугольную форму для вертикальной черты фиксированного размера или горизонтального и вертикального.  Когда пользователь перетаскивает углы или стороны, структура перевернет между 2 позволенными конфигурациями высоты и ширины.  
  
 Правило класс, производный от границ <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>.  Экземпляр правила создается в фигуре:  
  
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
  
 Обратите внимание на то, что и расположение и размеры могут быть ограничены, если необходимо.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)