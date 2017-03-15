---
title: "При использовании аргумента типа Object используйте метод FileGetObject вместо метода FileGet | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# При использовании аргумента типа Object используйте метод FileGetObject вместо метода FileGet
Метод `FileGet` включает аргумент типа `Object`. Чтобы избежать неоднозначности, следует использовать `FileGetObject` вместо `FileGet`.  
  
 Обратите внимание, что функциональные возможности, предлагаемые `My.Computer.Filesystem`, проще в использовании и обеспечивают большую производительность, чем `FileGet` или `FileGetObject`.  
  
### Исправление ошибки  
  
1.  Замените `FileGet` объектом `FileGetObject`.  
  
2.  Приведите аргумент `Object` к более конкретному типу.  
  
## См. также  
 [НЕ В СБОРКЕ. Функция FileGetObject](http://msdn.microsoft.com/ru-ru/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)   
 [Объект My.Computer.FileSystem](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)