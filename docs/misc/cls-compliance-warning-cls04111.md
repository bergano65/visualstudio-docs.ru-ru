---
title: "Предупреждение о соответствии спецификации CLS CLS04111 | Microsoft Docs"
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
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS04111
Атрибуты должны иметь тип System::Attribute или наследоваться от него  
  
 Чтобы соответствовать спецификации CLS, пользовательский атрибут должен наследоваться от System::Attribute.  К типу был применен атрибут, не наследующий от System::Attribute.  
  
 В следующем объявлении \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS04111:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Наследование атрибута от System::Attribute позволяет устранить предупреждение:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```