---
title: "Атрибут &quot;Microsoft.VisualBasic.ComClassAttribute&quot; указан для класса &quot;&lt;имя_класса&gt;&quot;, но он не имеет общих членов, которые могут быть предоставлены в COM; таким образом, интерфейсы COM не создаются. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40011"
  - "vbc40011"
helpviewer_keywords: 
  - "BC40011"
ms.assetid: 39aed273-bf27-4667-8116-022c4dd8f3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут &quot;Microsoft.VisualBasic.ComClassAttribute&quot; указан для класса &quot;&lt;имя_класса&gt;&quot;, но он не имеет общих членов, которые могут быть предоставлены в COM; таким образом, интерфейсы COM не создаются.
Класс, использующий блок атрибутов `COMClassAttribute`, не определяет никакие свойства или методы `Public`. Если класс должен быть предоставлен как COM\-объект, все его свойства и методы должны быть объявлены с уровнем доступа `Public`.  
  
 Данное сообщение является предупреждением по умолчанию. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40011  
  
### Исправление ошибки  
  
-   Добавьте ключевое слово `Public` в одно или несколько свойств или методов в классе или удалите блок атрибутов `COMClassAttribute`.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)   
 [Класс ComClassAttribute](http://msdn.microsoft.com/ru-ru/5c2f0835-9210-47dc-bc59-5c1769953574)