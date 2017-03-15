---
title: "Не удается инициализировать свойство &quot;&lt;имя_свойства&gt;&quot; в выражении инициализатора объекта, поскольку необходимо наличие в нем аргументов | Microsoft Docs"
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
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается инициализировать свойство &quot;&lt;имя_свойства&gt;&quot; в выражении инициализатора объекта, поскольку необходимо наличие в нем аргументов
Члены, инициализированные в списке инициализаторов объекта, должны быть полями или свойствами, и у членов свойства не может быть параметров. Например, для свойств по умолчанию требуются аргументы, поэтому они не могут быть инициализированы в списке инициализаторов объекта. Дополнительные сведения см. в разделе [НЕ В СБОРКЕ. Свойства по умолчанию](http://msdn.microsoft.com/ru-ru/a70f2a27-8176-4858-935e-f25afdd43ab5).  
  
 **Идентификатор ошибки:** BC30992  
  
### Исправление ошибки  
  
-   Удалите из списка инициализации все свойства, имеющие аргументы.  
  
## Пример  
 В приведенном ниже классе содержится используемое по умолчанию свойство `defaultProp`, для которого требуется целочисленный аргумент.  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 Так как для свойства по умолчанию требуется аргумент, следующее объявление вызывает ошибку:  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## См. также  
 [НЕ В СБОРКЕ. свойства по умолчанию](http://msdn.microsoft.com/ru-ru/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [НЕ В СБОРКЕ. свойства и процедуры свойств](http://msdn.microsoft.com/ru-ru/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)