---
title: "Предупреждение о соответствии спецификации CLS CLS01201 | Microsoft Docs"
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
  - "CLS01201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01201"
ms.assetid: 8c3e6ce4-8ea5-487a-bbed-56a36eceb024
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01201
Видимость и доступность типов и членов должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член. Например, открытый конструктор, видимый за пределами его сборки, не должен иметь аргументов, типы которых видимы только в пределах сборки.  
  
 Типы в сигнатурах конструктора должны иметь уровень доступности не ниже уровня доступности конструктора.  Например, открытый конструктор, видимый за пределами его сборки, не должен иметь аргументов, типы которых видимы только в пределах сборки.  
  
 Дополнительные сведения о проверке CLS\-совместимости см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем примере возникает ошибка CLS01201:  
  
```  
/* CLS01201.cpp */ // compile with: /clr /LD // CLS01201 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private ref class AssemblyLevelType {}; public ref class One { public: One(AssemblyLevelType^ parameter) {}   // not cls compliant }; private value class Two { public: Two(AssemblyLevelType^ parameter) {}   // OK };  
```