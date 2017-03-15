---
title: "&lt;спецификатор1&gt; &lt;тип&gt; не может наследовать от &lt;спецификатор2&gt; &lt;тип&gt;, поскольку он расширяет доступ базового &lt;тип&gt;. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30509"
  - "vbc30509"
helpviewer_keywords: 
  - "BC30509"
ms.assetid: 53594d6e-5e6d-463d-aa68-e2d41e152da7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;спецификатор1&gt; &lt;тип&gt; не может наследовать от &lt;спецификатор2&gt; &lt;тип&gt;, поскольку он расширяет доступ базового &lt;тип&gt;.
Предпринята попытка наследования открытым классом от базового класса, помеченного ключевым словом `Private` или `Friend`.  
  
 **Идентификатор ошибки:** BC30509  
  
### Исправление ошибки  
  
-   Объявите базовый класс как `Public` или объявите наследующий класс как `Private` или `Friend`.  
  
## См. также  
 [НЕ В СБОРКЕ. Наследование в Visual Basic](http://msdn.microsoft.com/ru-ru/e5e6e240-ed31-4657-820c-079b7c79313c)