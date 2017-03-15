---
title: "В выражениях для операторов &quot;Select&quot;, &quot;Case&quot; используются операнды типа Object; возможна ошибка времени выполнения. | Microsoft Docs"
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
  - "vbc42036"
  - "bc42036"
helpviewer_keywords: 
  - "BC42036"
ms.assetid: f11e9c9f-aa66-4eb1-8f49-abf713bef885
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В выражениях для операторов &quot;Select&quot;, &quot;Case&quot; используются операнды типа Object; возможна ошибка времени выполнения.
Конструкция `Select`...`Case` использует одно или несколько выражений [Тип данных Object](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Когда переменная или выражение вычисляется как `Object`, компилятор должен осуществить *позднее связывание*, что вызывает дополнительные операции во время выполнения. Это также подвергает ваше приложение риску ошибок времени выполнения. Например, если присвоить <xref:System.Windows.Forms.Form> переменной `Object` и попытаться сравнить ее с числом, то среда выполнения создаст исключение <xref:System.InvalidCastException>, так как Visual Basic не может преобразовать объект <xref:System.Windows.Forms.Form> в числовое значение.  
  
 Все выражения в конструкции `Select`...`Case` должны иметь один и тот же тип данных или близкие типы данных, которые могут быть преобразованы друг в друга. Это требование объясняется тем, что каждый оператор `Case` сравнивает хотя бы одно значение с тестовым выражением, на котором построена конструкция `Select`...`Case`.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42036  
  
### Исправление ошибки  
  
-   Если это возможно, упорядочите все выражения для оценки в типах данных, для которых определены операторы сравнения.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Арифметические операторы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Операторы сравнения в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)