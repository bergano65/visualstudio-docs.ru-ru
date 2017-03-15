---
title: "Типы данных параметров типа в методе расширения &quot;&lt;имя_метода&gt;&quot;, определенные в &quot;&lt;имя_типа&gt;&quot;, не могут быть получены из этих аргументов | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36646"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы данных параметров типа в методе расширения &quot;&lt;имя_метода&gt;&quot;, определенные в &quot;&lt;имя_типа&gt;&quot;, не могут быть получены из этих аргументов
Типы данных параметров типа в методе расширения "\<имя\_метода\>", определенные в "\<имя\_типа\>", не могут быть получены из этих аргументов. Эту ошибку может исправить явное указание типов данных.  
  
 Предпринята попытка использования определения типов для определения типа \(или типов\) данных параметра \(или параметров\) типа при оценке вызова универсального метода расширения. Однако компилятору не удается найти тип данных для параметров типа в этом методе, и он сообщает об ошибке.  
  
> [!NOTE]
>  Когда указание аргументов является обязательным \(например, в операторах выражений запросов\), это сообщение об ошибке появляется без второй фразы.  
  
 Эта ошибка демонстрируется в приведенном ниже коде.  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **Идентификатор ошибки:** BC36649 и BC36646  
  
### Исправление ошибки  
  
-   Попробуйте указать тип данных для параметра или параметров типа, вместо того чтобы полагаться на определение типа.  
  
## См. также  
 [Неявное преобразование делегата](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)