---
title: "Предупреждение компилятора (уровень 2) CS1698 | Microsoft Docs"
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
  - "CS1698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1698"
ms.assetid: 65cac5d0-e045-40f9-911c-1bf50e710b18
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS1698
Циклическая ссылка на сборку "имя\_сборки1" не совпадает с выходным именем сборки "имя\_сборки2". Попробуйте добавить ссылку на "имя\_сборки1" или соответствующим образом изменить имя результирующей сборки.  
  
 Предупреждение CS1698 возникает при неправильной ссылке на сборку. Это может произойти, если сборка, на которую указывает ссылка, скомпилирована повторно. Чтобы устранить эту проблему, не заменяйте сборку, зависимую от сборки, на которую выполняется ссылка.  
  
## Пример  
  
```  
// CS1698_a.cs // compile with: /target:library /keyfile:mykey.snk [assembly:System.Reflection.AssemblyVersion("2")] public class CS1698_a {}  
```  
  
## Пример  
  
```  
// CS1698_b.cs // compile with: /target:library /reference:CS1698_a.dll /keyfile:mykey.snk public class CS1698_b : CS1698_a {}  
```  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS1698.  
  
```  
// CS1698_c.cs // compile with: /target:library /out:cs1698_a.dll /reference:cs1698_b.dll /keyfile:mykey.snk // CS1698 expected [assembly:System.Reflection.AssemblyVersion("3")] public class CS1698_c : CS1698_b {} public class CS1698_a {}  
  
```