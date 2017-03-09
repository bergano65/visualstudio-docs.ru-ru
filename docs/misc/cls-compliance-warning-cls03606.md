---
title: "Предупреждение о соответствии спецификации CLS CLS03606 | Microsoft Docs"
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
  - "CLS03606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03606"
ms.assetid: 567b0b18-7487-4f48-a9ae-a4a4db53a409
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS03606
Глобальные статические методы несовместимы с CLS  
  
 Глобальные статические \(static\) поля и методы не совместимы с CLS.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем примере возникает ошибка CLS03606:  
  
```  
// CLS03606.cpp // compile with: /clr /LD // CLS03606 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; void MyGlobalFunction1() {}   // CLS03606 public ref class MyClass { public: void MemberFunction() {}   // OK };  
```