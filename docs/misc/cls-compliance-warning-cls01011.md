---
title: "Предупреждение о соответствии спецификации CLS CLS01011 | Microsoft Docs"
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
  - "CLS01011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01011"
ms.assetid: e4141e15-14fd-491c-9639-f3f3a47d7865
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01011
Доступность не должна изменяться при переопределении унаследованных методов  
  
 Убедитесь, что переопределяющий метод имеет ту же видимость, что и метод, который он переопределяет.  При переопределении унаследованных методов не должна изменяться доступность. Исключение составляют методы, унаследованные из другой сборки с доступностью Family\-or\-Assembly. В таких случаях переопределенный метод должен иметь доступность Family.  
  
 Дополнительные сведения о проверке CLS\-совместимости см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем примере возникает ошибка CLS01011:  
  
```  
// CLS01011.cpp // compile with: /clr /LD // CLS01011 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class BaseType { public protected: virtual void BaseTypeMethod() {} }; public ref class One : public BaseType { public: void BaseTypeMethod() {}   // CLS01011 // OK // public protected: //    void BaseTypeMethod() {} };  
```