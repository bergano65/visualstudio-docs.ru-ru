---
title: "Предупреждение о соответствии спецификации CLS CLS01214 | Microsoft Docs"
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
  - "CLS01214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01214"
ms.assetid: 5968af20-3d3e-4c7b-ad61-c06979cc9efd
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01214
Видимость и доступность типов и членов должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член. Например, делегат, видимый за пределами его сборки, не должен иметь аргументов, типы которых видимы только в пределах сборки.  
  
 Типы в сигнатурах делегата должны иметь доступность большую или равную доступности делегата.  Например, делегат, видимый за пределами его сборки, не должен иметь аргументов, типы которых видимы только в пределах сборки.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS01214:  
  
```  
/* CLS01214.cpp */ // compile with: /clr /LD // CLS01214 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicType {}; private ref class AssemblyType {}; public delegate PublicType^ AssemblyDelegate(AssemblyType^ parameter);   // not cls compliant public delegate PublicType^ AssemblyDelegate2(PublicType^ parameter);   //cls compliant  
```