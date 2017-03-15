---
title: "Предупреждение компилятора (уровень 2) CS0440 | Microsoft Docs"
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
  - "CS0440"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0440"
ms.assetid: ade6761f-4d7d-42bc-a0c5-bbb1b987a1aa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS0440
Определение псевдонима с именем "global" не рекомендуется из\-за того, что "global::" всегда указывает на глобальное пространство имен и не является псевдонимом.  
  
 Это предупреждение возникает при определении псевдонима с именем global.  
  
## Пример  
 В следующем примере возникает ошибка CS0440:  
  
```  
// CS0440.cs // Compile with: /W:1 using global = MyClass;   // CS0440 class MyClass { static void Main() { // Note how global refers to the global namespace // even though it is redefined above. global::System.Console.WriteLine(); } }  
```