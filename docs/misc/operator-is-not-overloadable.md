---
title: "Оператор не поддерживает перегрузку | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33002"
  - "bc33002"
helpviewer_keywords: 
  - "BC33002"
ms.assetid: 8628ea42-57d8-41ca-8bdc-5e4c27be543e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор не поддерживает перегрузку
Не все операторы подходят для перегрузки. В приведенной ниже таблице перечислены операторы, которые можно определить.  
  
|Тип|Операторы|  
|---------|---------------|  
|Унарный|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Преобразование \(унарный\)|`CType`|  
  
 Обратите внимание на то, что оператор `=` в списке бинарных операторов является оператором сравнения, а не оператором присваивания.  
  
 **Идентификатор ошибки:** BC33002  
  
### Исправление ошибки  
  
1.  Выберите оператор из набора перегружаемых операторов.  
  
2.  Если требуется возможность перегрузки оператора, который нельзя перегрузить непосредственно, создайте процедуру `Function`, которая принимает соответствующие параметры и возвращает соответствующее значение.  
  
## См. также  
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement)