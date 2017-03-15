---
title: "Все поля, за исключением последнего элемента, должны иметь ширину больше нуля | Microsoft Docs"
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
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Все поля, за исключением последнего элемента, должны иметь ширину больше нуля
Все поля, за исключением последнего элемента, должны иметь ширину больше нуля. Ширина поля, меньшая или равная нулю в последнем элементе, указывает, что поле имеет переменную длину.  
  
 Операция не была выполнена, так как ширина поля, отличного от последнего элемента, задана равной нулю или меньше. Ширина поля, меньшая или равная нулю, может использоваться в последнем элементе для указания на то, что последнее поле имеет переменную длину, но не может использоваться как любой другой элемент.  
  
### Исправление ошибки  
  
-   Задайте для ширины поля корректное значение.  
  
## См. также  
 [Метод TextFieldParser.SetFieldWidths](http://msdn.microsoft.com/ru-ru/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [Свойство TextFieldParser.FieldWidths](http://msdn.microsoft.com/ru-ru/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [Практическое руководство. Чтение из текстовых файлов с фиксированной шириной полей](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [Объект TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)