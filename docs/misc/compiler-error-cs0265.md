---
title: "Ошибка компилятора CS0265 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0265"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0265"
ms.assetid: d43d19c2-8a66-4bb1-95a0-557b0a29bce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0265
Частичные объявления "тип" содержат непоследовательные ограничения для параметра типа "параметр типа"  
  
 Эта ошибка возникает при определении универсального класса как разделяемого класса, так что его разделяемые определения образуются в нескольких местах и ограничения универсального типа становятся несогласованными или отличаются в двух и более местах. При указании ограничений в нескольких местах они должны быть одинаковыми. Наиболее простым решением будет задать ограничения в одном месте и опустить их во всех остальных. Дополнительные сведения см. в разделах [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) и [Ограничения параметров типа](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
 Приведенный ниже код вызывает ошибку CS0265.  
  
## Пример  
 В этом коде все разделяемые определения класса расположены в одном файле, но могут распространяться по нескольким файлам.  
  
```  
// CS0265.cs public class GenericsErrors { interface IFace1 { } interface IFace2 { } partial class PartialBadBounds<T> where T : IFace1 { } // CS0265 partial class PartialBadBounds<T> where T : IFace2 { } }  
```