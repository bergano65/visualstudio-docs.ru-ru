---
title: "Предупреждение о соответствии спецификации CLS CLS04104 | Microsoft Docs"
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
  - "CLS04104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04104"
ms.assetid: 89a5c080-c7f3-48b5-b2ff-90aa2236c90e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS04104
Атрибуты должны иметь тип "System::Attribute" или наследоваться от него  
  
 Чтобы соответствовать спецификации CLS, пользовательский атрибут должен наследоваться от System::Attribute.  К функции\-члену был применен атрибут, не наследуемый от System::Attribute.  
  
 В следующем объявлении \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS04111:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Затем показана функция\-член, которая использует этот атрибут:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 00 00 00 00 00 00 )  
```  
  
 Наследование атрибута от System::Attribute позволяет устранить предупреждение:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```