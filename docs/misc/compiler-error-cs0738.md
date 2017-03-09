---
title: "Ошибка компилятора CS0738 | Microsoft Docs"
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
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0738
"имя типа" не реализует член интерфейса "имя члена". "имя\_метода" не может реализовать "член\_интерфейса", потому что не имеет соответствующего возвращаемого типа "имя\_типа".  
  
 Возвращаемое значение реализующего метода в классе должно соответствовать возвращаемому значению члена интерфейса, который он реализует.  
  
### Исправление ошибки  
  
1.  Измените возвращаемый тип метода в соответствии с типом члена интерфейса.  
  
## Пример  
 При компиляции следующего кода возникнет ошибка CS0738, так как метод класса возвращает `void`, а член интерфейса с тем же именем возвращает `int`:  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## См. также  
 [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)