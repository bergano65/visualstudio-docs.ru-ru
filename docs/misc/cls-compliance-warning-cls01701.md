---
title: "Предупреждение о соответствии спецификации CLS CLS01701 | Microsoft Docs"
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
  - "CLS01701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01701"
ms.assetid: 6ccbe156-9017-44ea-bd4e-a838af2ec2e7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01701
Типы неуправляемых указателей не являются CLS\-совместимыми  
  
 CLS\-совместимый конструктор не может содержать объявление собственного указателя.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS01701:  
  
```  
// CLS01701.cpp // compile with: /clr /LD // CLS01701 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: One(int* Parameter) {}   // CLS01701 };  
```