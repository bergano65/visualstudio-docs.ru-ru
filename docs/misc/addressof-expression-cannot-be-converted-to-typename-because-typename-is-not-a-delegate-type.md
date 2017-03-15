---
title: "Выражение AddressOf не может быть преобразовано в тип &quot;&lt;имя_типа&gt;&quot;, так как &quot;&lt;имя_типа&gt;&quot; не является типом делегата. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30581"
  - "bc30581"
helpviewer_keywords: 
  - "BC30581"
ms.assetid: 5db7589a-5456-4b3a-9d6b-93d9157f0484
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Выражение AddressOf не может быть преобразовано в тип &quot;&lt;имя_типа&gt;&quot;, так как &quot;&lt;имя_типа&gt;&quot; не является типом делегата.
Оператор пытается преобразовать выражение `AddressOf` в тип, который не является типом делегата.  
  
 Оператор `AddressOf` создает экземпляр делегата процедуры, ссылающийся на конкретную процедуру. Выражение `AddressOf` может использоваться в качестве операнда конструктора делегата, или оно может использоваться в контексте, в котором тип делегата может определяться компилятором.  
  
 **Идентификатор ошибки:** BC30581  
  
### Исправление ошибки  
  
-   Измените целевой тип на тип делегата.  
  
## См. также  
 [Оператор AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)