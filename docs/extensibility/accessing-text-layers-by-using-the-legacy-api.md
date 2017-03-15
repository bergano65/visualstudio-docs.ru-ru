---
title: "Доступ к текстовые слои с помощью API прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - слои текста"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Доступ к текстовые слои с помощью API прежних версий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Уровень текста обычно инкапсулирует определенный аспект макета текста.  Например, hide уровня функция\-на \-\- "Time" вставке СМС до и после функцией, содержащий знак вставки \(точка вставки текста\).  
  
 Уровень текст находится между буфером и представлением, и он изменяет способ представления см. в разделе содержимое буфера.  
  
## Данные слоя текста  
 Следующий список описывает уровни текст работают в пределах [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Текст на уровне текст можно оформлять с расцветкой и метками.  
  
-   В данный момент невозможно реализовать собственные уровни.  
  
-   Предоставляет уровня <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, из которого наследуется  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>.  Текстовый буфер является также реализован как уровень, который обеспечивает представление, чтобы обрабатывать полиморфно с основными уровнями.  
  
-   Любое количество уровней может лежать между представлением и буфером.  Каждый уровень имеет дело только с уровнем под ним и представление связано во многом с уровнем верхнего уровня.  \(Представление имеет некоторые сведения о буфере.\)  
  
-   Слой может влиять только на уровни, под ним.  Он не может повлиять на уровень выше его за по данной точке стандартные события.  
  
-   В редакторе, скрытый текст, синтетическое текста и перенос по словам реализованы как уровни.  Можно реализовать скрытое и синтетическое текста, не работать непосредственно с уровнями.  Дополнительные сведения см. в разделах [Структуризация в языковую службу для прежних версий](../extensibility/internals/outlining-in-a-legacy-language-service.md) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Каждый слой текста имеет собственную локальной системе координат, которая доступна через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> интерфейс.  Уровень линия\-использованих программы\-оболочек, например может содержать 2 линии, пока основной текстовый буфер может содержать только одну линию.  
  
-   Взаимодействует со слоями через представление <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> интерфейс.  Используйте этот интерфейс, чтобы согласовать координаты представления с координатами буфера.  
  
-   Любой уровень, как синтетический уровень текст, исходящий текст должен предоставить реализацию local <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Кроме <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>текст, уровень должен реализовать  <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> события и char  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> интерфейс.  
  
## См. также  
 [В редакторах синтаксиса](../extensibility/syntax-coloring-in-custom-editors.md)   
 [С помощью текстовых маркеров с API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Настройка меню и элементы управления редактора с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)