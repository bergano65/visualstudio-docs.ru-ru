---
title: "Предупреждение компилятора (уровень&#160;1) CS3004 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3004"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3004"
ms.assetid: 84aa3b44-42b7-4d31-82b8-386e56f88129
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS3004
Смешанные и разложенные знаки Юникода не удовлетворяют требованиям CLS  
  
 В соответствии со спецификацией CLS в идентификаторах [public](/dotnet/csharp/language-reference/keywords/public), [protected](/dotnet/csharp/language-reference/keywords/protected) или `protected` `internal` допускаются только составные символы ЮНИКОДА. Дополнительные сведения о соответствии CLS см. в разделах [Написание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3) и [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).