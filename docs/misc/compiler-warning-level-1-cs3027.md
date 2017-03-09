---
title: "Предупреждение компилятора (уровень 1) CS3027 | Microsoft Docs"
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
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS3027
"тип\_1" несовместим с CLS, поскольку с ним несовместим базовый интерфейс "тип\_2"  
  
 Тип, несовместимый с CLS, не может быть базовым типом для типа, совместимого с CLS.  
  
## Пример  
 Следующий пример содержит интерфейс с методом, использующим тип, сигнатура которого несовместима с CLS, что делает тип несовместимым с CLS.  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## Пример  
 При компиляции следующего примера будет выдано предупреждение CS3027.  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```