---
title: "Типы данных параметров типа в методе &quot;&lt;имя_метода&gt;&quot; не могут выводиться из этих аргументов | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36645"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы данных параметров типа в методе &quot;&lt;имя_метода&gt;&quot; не могут выводиться из этих аргументов
Типы данных параметров типа в методе "\<имя\_метода\>" не могут выводиться из этих аргументов. Явное указание типов данных может исправить эту ошибку.  
  
 Предпринята попытка использования определения типов для определения типа \(или типов\) параметра \(или параметров\) типа во время определения вызова универсальной процедуры. Однако в этом методе компилятору не удается найти тип данных для параметров типа и он сообщает об ошибке.  
  
> [!NOTE]
>  Когда аргументы являются обязательными \(например, в операторах выражений запросов\), это сообщение об ошибке отображается без второго предложения.  
  
 Эта ошибка показана в приведенном ниже коде.  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **Идентификатор ошибки:** BC36648 и BC36645  
  
### Исправление ошибки  
  
-   Попробуйте указать тип данных для параметра или параметров типа, вместо того чтобы полагаться на определение типа.  
  
## См. также  
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)