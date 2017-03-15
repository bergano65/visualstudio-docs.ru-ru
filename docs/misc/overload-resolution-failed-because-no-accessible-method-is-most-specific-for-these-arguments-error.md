---
title: "Не удалось разрешить перегрузку, так как ни один из доступных &quot;&lt;method&gt;&quot; не является наиболее подходящим для этих аргументов: &lt;error&gt; | Microsoft Docs"
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
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "сбой разрешения"
  - "BC30521"
  - "сбой при разрешении перегрузки"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удалось разрешить перегрузку, так как ни один из доступных &quot;&lt;method&gt;&quot; не является наиболее подходящим для этих аргументов: &lt;error&gt;
Вы выполнили вызов перегруженного метода, однако компилятор обнаружил как минимум две перегрузки со списками параметров, в которые можно преобразовать ваш список аргументов, и не удается выбрать один из них.  
  
 Компилятор пытается сопоставить типы данных в списке аргументов вызова и в списке параметров перегрузки настолько близко, насколько возможно. Он требует расширяющего преобразования от каждого вашего аргумента в его соответствующий параметр, независимо от того, имеет ли ключ проверки типа \([Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) значение `On` или `Off`.  
  
 Если компилятор обнаруживает несколько перегрузок, отвечающих расширяющим требованиям, то далее он ищет перегрузку, наиболее подходящую для типов данных аргументов, то есть вызывающую наименьший объем расширения. Он создает это сообщение об ошибке, когда одна перегрузка больше подходит для типа данных одного аргумента, а другая перегрузка больше подходит для типа данных другого аргумента. Дополнительные сведения и пример см. в разделе [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 **Идентификатор ошибки:** BC30521  
  
### Исправление ошибки  
  
1.  Просмотрите все перегрузки для метода и определите, какую из них вы хотите вызвать.  
  
2.  В инструкции вызова сделайте типы данных аргументов соответствующими типам данных параметров, определенных для нужной перегрузки. Возможно, потребуется использовать [Функция CType](/dotnet/visual-basic/language-reference/functions/ctype-function) для преобразования одного или нескольких типов данных в определенные типы.  
  
## См. также  
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Разрешение перегрузки](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Перегруженные свойства и методы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Функция CType](/dotnet/visual-basic/language-reference/functions/ctype-function)