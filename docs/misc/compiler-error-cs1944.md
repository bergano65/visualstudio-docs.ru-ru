---
title: "Ошибка компилятора CS1944 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1944"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1944"
ms.assetid: e5e2c018-9a7e-48ee-8dd3-98e3553777c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1944
Дерево выражения не может содержать небезопасные операции над указателями.  
  
 Деревья выражений не поддерживают типы указателей, поскольку метод <xref:System.Linq.Expressions.Expression%601.Compile%2A?displayProperty=fullName> допускается только для создания проверяемого кода. См. комментарии.  
  
### Исправление ошибки  
  
1.  Не используйте типы указателей при попытке создания дерева выражений.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1944:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 В некоторых случаях допустимо иметь указатели в деревьях выражений. Рассмотрим следующий пример кода:  
  
 `Expression<Func\<int*[], int*[]>) e = (int*[] i)=>i;`  
  
 Этот код представляет собой допустимое дерево выражений, так как никакие аргументы типа не являются типами указателей. Они представляют собой массивы указателей, и массивы не являются типами указателей. Кроме того, текст дерева выражения не выполняет никаких опасных операций над указателями.  
  
## См. также  
 [небезопасное](/dotnet/csharp/language-reference/keywords/unsafe)