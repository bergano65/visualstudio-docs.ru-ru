---
title: "&quot;Catch&quot; не может перехватить тип &quot;&lt;имя_типа&gt;&quot;, так как он не является типом &quot;System.Exception&quot; или классом, наследующим от &quot;System.Exception&quot;. | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Catch&quot; не может перехватить тип &quot;&lt;имя_типа&gt;&quot;, так как он не является типом &quot;System.Exception&quot; или классом, наследующим от &quot;System.Exception&quot;.
`Catch` может перехватывать только исключения, и была предпринята попытка перехвата объекта, не являющегося производным от исключения.  
  
 **Идентификатор ошибки:** BC30392  
  
### Исправление ошибки  
  
1.  Удалите оператор `Catch` или измените целевой объект оператора `Catch` на действительное исключение.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Общие сведения о структурированной обработке исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)