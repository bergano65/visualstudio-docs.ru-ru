---
title: "Параметр типа нельзя использовать в предложении Implements | Microsoft Docs"
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
  - "vbc32056"
  - "bc32056"
helpviewer_keywords: 
  - "BC32056"
ms.assetid: a62d773b-e878-4817-8638-da49849477d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа нельзя использовать в предложении Implements
Предложение `Implements` в универсальном типе определяет параметр типа как реализуемый член.  
  
 В предложении `Implements` должны указываться интерфейс и член. Параметр типа может быть передан в интерфейс, но его нельзя передать члену или использовать в качестве имени члена.  
  
 Эта ошибка может быть вызвана указанными ниже операторами.  
  
```  
Class c1(Of t) Implements i1(Of t) Public Sub doSomething() Implements t End Class  
```  
  
 **Идентификатор ошибки:** BC32056  
  
### Исправление ошибки  
  
-   Укажите имя интерфейса и подлинный член интерфейса после ключевого слова `Implements`. При необходимости можно передать параметр типа в интерфейс.  
  
    ```  
    Public Sub doSomething() Implements i1(Of t).doSomething  
    ```  
  
## См. также  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [НЕ В СБОРКЕ. ключевое слово Implements и оператор Implements](http://msdn.microsoft.com/ru-ru/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)