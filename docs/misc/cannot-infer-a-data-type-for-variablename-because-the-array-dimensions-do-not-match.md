---
title: "Не удается вывести тип данных для &quot;&lt;имя_переменной&gt;&quot; из-за несоответствия размерности массивов. | Microsoft Docs"
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
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается вывести тип данных для &quot;&lt;имя_переменной&gt;&quot; из-за несоответствия размерности массивов.
Если размерность, используемая для инициализации массива, не соответствует размерности в объявлении, компилятор не может вывести тип данных для массива. Например, следующий код вызывает эту ошибку.  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **Идентификатор ошибки:** BC36909  
  
## См. также  
 [Вывод локального типа](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [НЕ В СБОРКЕ. Практическое руководство. Инициализация многомерного массива](http://msdn.microsoft.com/ru-ru/502dcf8b-d86c-46f1-ad7d-3ce809645774)