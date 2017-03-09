---
title: "Выражение &quot;AddressOf&quot; не может быть преобразовано в &quot;&lt;имя_типа&gt;&quot;, поскольку тип &quot;&lt;имя_типа&gt;&quot; объявлен как &quot;MustInherit&quot; и не может быть создан. | Microsoft Docs"
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
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Выражение &quot;AddressOf&quot; не может быть преобразовано в &quot;&lt;имя_типа&gt;&quot;, поскольку тип &quot;&lt;имя_типа&gt;&quot; объявлен как &quot;MustInherit&quot; и не может быть создан.
Оператор пытается преобразовать выражение `AddressOf` в тип, который может быть только базовым классом и не может использоваться для создания экземпляра.  
  
 Оператор `AddressOf` создает экземпляр делегата процедуры, ссылающийся на конкретную процедуру.  
  
 **Идентификатор ошибки:** BC30939  
  
### Исправление ошибки  
  
-   Назначьте выражение `AddressOf` определенному типу делегата.  
  
## См. также  
 [Оператор AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Делегаты](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)