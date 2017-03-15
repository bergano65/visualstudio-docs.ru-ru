---
title: "Предупреждение о соответствии спецификации CLS CLS01203 | Microsoft Docs"
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
  - "CLS01203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01203"
ms.assetid: fe27463a-27df-473b-985a-b04c3bfac4d3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01203
Видимость и доступность типов и членов должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член. Например, общее поле, видимое за пределами его сборки, не должно иметь тип, видимый только в пределах сборки.  
  
 Видимость и доступность типов и членов должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член. Например, общее поле, видимое за пределами его сборки, не должно иметь тип, видимый только в пределах сборки.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению ошибки CLS01203:  
  
```  
/* CLS01203.cpp */ // compile with: /clr /LD // CLS01203 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Member1;   // not cls compliant PublicLevelType^ Member2;   // cls compliant };  
```