---
title: "&quot;&lt;метод1&gt;&quot; не может переопределять &quot;&lt;метод2&gt;&quot;, т.&#160;к является оператором &quot;Declare&quot; | Microsoft Docs"
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
  - "vbc30474"
  - "bc30474"
helpviewer_keywords: 
  - "BC30474"
ms.assetid: 7277e8cc-aa3c-40c3-8682-c8c42d2ee921
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;метод1&gt;&quot; не может переопределять &quot;&lt;метод2&gt;&quot;, т.&#160;к является оператором &quot;Declare&quot;
Предпринята попытка переопределения делегата в имени базового класса, объявленного с помощью оператора `Declare`.  
  
 **Идентификатор ошибки:** BC30474  
  
### Исправление ошибки  
  
1.  Измените переопределяемый член так, чтобы он не являлся оператором `Declare`.  
  
2.  Не пытайтесь переопределить этот метод.  
  
## См. также  
 [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)