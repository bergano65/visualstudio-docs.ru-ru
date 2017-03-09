---
title: "Предупреждение о соответствии спецификации CLS CLS04114 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS04114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04114"
ms.assetid: 84285fbb-ecd1-46e6-9bdb-dc44db40dcc0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS04114
Атрибуты должны иметь тип "System::Attribute" или наследоваться от него  
  
 Чтобы соответствовать спецификации CLS, пользовательский атрибут должен наследоваться от System::Attribute.  К делегату был применен атрибут, не наследуемый от System::Attribute.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [Сборки, соответствующие CLS](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем объявлении \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS04100:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Затем показан делегат, который использует атрибут:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Наследование атрибута от System::Attribute позволяет устранить предупреждение:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```