---
title: "После MyBase должна быть указана точка (&quot;.&quot;) и идентификатор | Microsoft Docs"
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
  - "bc32027"
  - "vbc32027"
helpviewer_keywords: 
  - "BC32027"
ms.assetid: 39e5512c-ef1e-46a3-a96c-277ea24bfee2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# После MyBase должна быть указана точка (&quot;.&quot;) и идентификатор
`MyBase` не является настоящей объектной переменной и не может использоваться самостоятельно. Эта переменная используется только для доступа к члену базового класса текущего экземпляра.  
  
 **Идентификатор ошибки:** BC32027  
  
### Исправление ошибки  
  
-   Если необходим доступ к члену, укажите оператор доступа к членам \(.\) и член базового класса после `MyBase`.  
  
-   Если доступ к члену не требуется, объявите и инициализируйте экземпляр базового класса или удалите ссылку на `MyBase`.  
  
## См. также  
 [MyBase — удалить](http://msdn.microsoft.com/ru-ru/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)