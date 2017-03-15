---
title: "&quot;&lt;имя1&gt;&quot; в Imports &quot;&lt;имя2&gt;&quot; не является ссылкой на пространство имен, класс, структуру, перечисление или модуль | Microsoft Docs"
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
  - "vbc30467"
  - "bc30467"
helpviewer_keywords: 
  - "BC30467"
ms.assetid: a4b8a23b-ba1b-44f7-9584-258dd2607581
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя1&gt;&quot; в Imports &quot;&lt;имя2&gt;&quot; не является ссылкой на пространство имен, класс, структуру, перечисление или модуль
Предпринята попытка использовать оператор `Imports` для элемента, не являющегося `Namespace`, `Class`, `Structure`, `Enum` или `Module`. Оператор `Imports` импортирует имена пространств имен из проектов и сборок, на которые имеются ссылки, или имена пространств имен, определенных в том же проекте, что и модуль, в котором находится данный оператор.  
  
 **Идентификатор ошибки:** BC30467  
  
### Исправление ошибки  
  
-   Проверьте импортируемый объект и убедитесь в том, что его можно импортировать с помощью оператора `Imports`.  
  
## См. также  
 [Оператор Imports \(пространство имен .NET и тип\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Ссылки и оператор Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NIB. Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)