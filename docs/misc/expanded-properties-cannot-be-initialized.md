---
title: "Невозможно инициировать расширенные свойства | Microsoft Docs"
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
  - "vbc36714"
  - "bc36714"
helpviewer_keywords: 
  - "BC36714"
ms.assetid: ba9408f3-e606-4749-8372-987999f405f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно инициировать расширенные свойства
Автоматически реализуемое свойство можно инициализировать в рамках его объявления, а расширенное свойство нельзя.  
  
 **Идентификатор ошибки:** BC36714  
  
### Исправление ошибки  
  
-   Используйте автоматически реализуемое свойство или удалите инициализацию из объявления свойства.  
  
## Пример  
 В следующих примерах показаны автоматически реализуемое свойство и расширенное свойство. Автоматически реализуемые свойства можно инициализировать с помощью присваивания или предложения `New`, а расширенные свойства нельзя.  
  
```vb#  
Class AutoImplementedExample ' An auto-implemented property can be assigned an initial value. Property IDNum As Integer = 33542 ' An auto-implemented property can be initialized with New. Property Name As New String("Don Hall") End Class Class ExpandedExample ' Attempting to expand an initialized auto-implemented property ' causes this error. 'Property IDNum As Integer = 33542 '    Get '    End Get '    Set(ByVal value As Integer) '    End Set 'End Property ' Instead, you can assign the initial value to the backing field. Private _IDNum As Integer = 33542 Property IDNum As Integer Get End Get Set(ByVal value As Integer) End Set End Property End Class  
```  
  
## См. также  
 [Автоматически реализуемые свойства](/dotnet/visual-basic/programming-guide/language-features/procedures/auto-implemented-properties)   
 [Практическое руководство. Создание свойства](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)