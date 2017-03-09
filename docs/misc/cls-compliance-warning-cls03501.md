---
title: "Предупреждение о соответствии спецификации CLS CLS03501 | Microsoft Docs"
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
  - "CLS03501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03501"
ms.assetid: 26a08830-9c8a-4bf6-931d-e0c523f1eb21
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS03501
В спецификации CLS запрещены модификаторы публично видимых обязательных элементов \(modreq\), но разрешены модификаторы необязательных элементов \(modopt\), которые не распознаются  
  
 В спецификации CLS запрещены модификаторы публично видимых обязательных элементов \(modreq\), но разрешены модификаторы необязательных элементов \(modopt\), которые не распознаются.  
  
 Убедитесь, что сигнатуры конструкторов не содержат типы, помеченные публично видимыми обязательными модификаторами.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS03501:  
  
```  
// CLS03501.cpp // compile with: /clr /LD // CLS03501 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: One(volatile Int32 param) {}   // CLS03501 One( Int32 param1, Int32 param2) {}   // OK };  
```