---
title: "Ошибка компилятора CS1017 | Microsoft Docs"
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
  - "CS1017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1017"
ms.assetid: e0902e8a-b042-4711-a8a6-83456a3f88cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1017
Конструкции catch не могут использоваться после универсальной конструкции catch оператора try  
  
 Блок `catch`, не имеющий параметров, должен находиться в конце серии блоков `catch`. Дополнительные сведения об исключениях см. в разделе [Операторы обработки исключений](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1017:  
  
```  
// CS1017.cs using System; namespace x { public class b : Exception { } public class a { public static void Main() { try { } catch   // CS1017, must be last catch { } catch(b) { throw; } } } }  
```