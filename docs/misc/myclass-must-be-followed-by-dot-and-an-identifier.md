---
title: "После MyClass должны следовать &quot;.&quot; и идентификатор | Microsoft Docs"
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
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# После MyClass должны следовать &quot;.&quot; и идентификатор
`MyClass` не является настоящей объектной переменной и не может использоваться самостоятельно. Эта переменная используется только для доступа к члену текущего экземпляра, как если бы он был `NotOverridable` \(не переопределяемым\) в базовом классе.  
  
 **Идентификатор ошибки:** BC32028  
  
### Исправление ошибки  
  
1.  Если необходим доступ к члену класса, укажите соответствующий оператор доступа к члену \(`.`\) и член текущего экземпляра после `MyClass`.  
  
2.  Если не требуется доступ к члену класса, используйте ключевое слово `Me`.  
  
## См. также  
 [MyClass — удалено](http://msdn.microsoft.com/ru-ru/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Me](http://msdn.microsoft.com/ru-ru/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)