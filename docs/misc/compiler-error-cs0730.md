---
title: "Ошибка компилятора CS0730 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0730"
ms.assetid: bf291285-dc1e-4c8d-a449-119004adc088
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0730
Невозможно перенаправить тип "тип", так как он является вложенным типом "тип".  
  
 Эта ошибка возникает при попытке перенаправить вложенный класс.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0730. Он состоит из двух файлов исходного кода. Сначала скомпилируйте файл библиотеки `CS0730a.cs`, а затем скомпилируйте файл `CS0730.cs`, ссылающийся на файл библиотеки.  
  
```  
// CS0730a.cs // compile with: /t:library public class Outer { public class Nested {} }  
```  
  
```  
// CS0730.cs // compile with: /t:library /r:CS0730a.dll using System.Runtime.CompilerServices; [assembly:TypeForwardedToAttribute(typeof(Outer.Nested))]   // CS0730 [assembly:TypeForwardedToAttribute(typeof(Outer))]   // OK  
```