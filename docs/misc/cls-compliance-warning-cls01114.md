---
title: "Предупреждение о соответствии CLS CLS01114 | Microsoft Docs"
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
  - "CLS01114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01114"
ms.assetid: f3382da6-d3d0-4209-a229-400701c53ede
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии CLS CLS01114
Все типы сигнатуры должны быть CLS\-совместимыми.  
  
 Если делегат является CLS\-совместимым, все типы в сигнатуре делегата должны быть CLS\-совместимыми.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению ошибки CLS01114:  
  
```  
// CLS01114.cpp // compile with: /clr /LD // CLS01114 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; // Public delegate public delegate CompliantType ^ PublicDelegate1(NotCompliantType^ param);   // CLS01114 public delegate CompliantType ^ PublicDelegate2(CompliantType^ param);   // OK  
```