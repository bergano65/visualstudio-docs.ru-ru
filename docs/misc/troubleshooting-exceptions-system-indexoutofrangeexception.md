---
title: "Разрешение вопросов, связанных с исключениями: System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "IndexOutOfRangeException - класс"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IndexOutOfRangeException
Исключение <xref:System.IndexOutOfRangeException> возникает при попытке доступа к элементу массива или коллекции с индексом, который находится вне границ массива или меньше нуля.  
  
## Полезные советы  
 **Убедитесь, что максимальный индекс списка не превышает размер списка**  
 Максимальный индекс списка должен быть меньше, чем размер списка.  
  
 **Убедитесь, что индекс не имеет отрицательное значение.**  
 Это исключение возникнет, если индекс меньше нуля.  
  
 **Убедитесь в правильности имен столбцов данных.**  
 Это исключение может возникнуть, если имя столбца данных, указанное в свойстве <xref:System.Data.DataView.Sort%2A?displayProperty=fullName>, неправильно. Дополнительные сведения см. в описании класса <xref:System.Data.DataView>.  
  
## Пример  
  
### Описание  
 В следующем примере используется блок `Try…Catch` для перехвата исключения `IndexOutOfRangeException`, когда индекс `i` оказывается за пределами границ массива \(от 0 до 3\). В примере показано следующее:  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### Код  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## См. также  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Массивы](/dotnet/visual-basic/programming-guide/language-features/arrays/index)