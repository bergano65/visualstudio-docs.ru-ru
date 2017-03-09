---
title: "Предупреждение о соответствии спецификации CLS CLS04101 | Microsoft Docs"
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
  - "CLS04101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04101"
ms.assetid: 5ad21eb4-0c6e-4629-bc4a-af274f8a8d90
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS04101
Атрибуты должны иметь тип "System::Attribute" или наследоваться от него  
  
 Убедитесь, что все атрибуты, примененные к параметрам конструктора, имеют тип "System.Attribute" или являются производными от него.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем объявлении \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS04101:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object { .method public specialname rtspecialname instance void  .ctor() cil managed  
```  
  
 Наследование атрибута от System::Attribute позволяет устранить предупреждение:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object { .method public specialname rtspecialname instance void  .ctor() cil managed  
```