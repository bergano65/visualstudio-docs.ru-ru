---
title: "Разрешение перегрузки не выполнено, поскольку ни один из доступных &quot;&lt;имя_универсальной_процедуры&gt;&quot; не принимает данное количество аргументов-типов | Microsoft Docs"
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
  - "bc32087"
  - "vbc32087"
helpviewer_keywords: 
  - "BC32087"
ms.assetid: a3eaafd3-80f6-4b7d-9b75-47b043fe17b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Разрешение перегрузки не выполнено, поскольку ни один из доступных &quot;&lt;имя_универсальной_процедуры&gt;&quot; не принимает данное количество аргументов-типов
Вызов перегруженной универсальной процедуры не может быть разрешен, так как компилятор не может получить доступ к перегруженной версии с соответствующим числом параметров типа.  
  
 При вызове универсальной процедуры необходимо указывать один аргумент типа для каждого параметра типа. Кроме того, можно не указывать аргументы типа и позволить компилятору попытаться выполнить *определение типа*. Дополнительные сведения см. в подразделе "Определение типа" в разделе [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Идентификатор ошибки:** BC32087  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что вызываемая версия является доступной для вызывающего кода. См. раздел [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels).  
  
2.  Добавьте или удалите аргументы типа из вызывающего кода таким образом, чтобы список аргументов типа совпадал со списком параметров типа версии, которую требуется вызвать.  
  
     \-или\-  
  
     Удалите все аргументы типа из вызывающего кода и позвольте компилятору попытаться выполнить определение типа. Необходимо иметь в виду, что при наличии конфликтов и неоднозначностей определение типа может завершиться ошибкой.  
  
## См. также  
 [Перегруженные свойства и методы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)