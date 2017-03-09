---
title: "Свойство &quot;&lt;имя_свойства&gt;&quot; не может быть инициализировано в выражении инициализации объекта, так как все его доступные перегрузки требуют аргументов | Microsoft Docs"
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
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство &quot;&lt;имя_свойства&gt;&quot; не может быть инициализировано в выражении инициализации объекта, так как все его доступные перегрузки требуют аргументов
Члены, инициализированные в списке инициализаторов объекта, должны быть полями или свойствами. Кроме того, у свойств в списке инициализаторов не может быть параметров. Свойство, вызывающее эту ошибку, перегружено, и каждая его версия требует аргументов. Поэтому его нельзя инициализировать в списке инициализаторов объекта.  
  
 **Идентификатор ошибки:** BC30993  
  
### Исправление ошибки  
  
-   Удалите из списка инициализаторов свойство, требующее аргументов.  
  
## Пример  
 Приведенный ниже класс содержит три определения свойств: одно для свойства `TotalItems` и два для свойства `Item`, которое является перегруженным.  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 Свойство `TotalItems` не требует аргументов и может быть инициализировано в списке инициализации объектов, как показано в приведенном ниже объявлении.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 Свойство `Item` перегружено, и каждая перегрузка требует аргумента. Поэтому свойство `Item` не может содержаться в списке инициализаторов объектов.  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 Чтобы избежать этой ошибки, инициализируйте свойство `Item` вне инициализатора объекта.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## См. также  
 [НЕ В СБОРКЕ. свойства и процедуры свойств](http://msdn.microsoft.com/ru-ru/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Практическое руководство. Вызов процедуры свойства](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. свойства по умолчанию](http://msdn.microsoft.com/ru-ru/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)