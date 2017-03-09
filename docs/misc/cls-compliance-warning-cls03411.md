---
title: "Предупреждение о соответствии CLS CLS03411 | Microsoft Docs"
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
  - "CLS03411"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03411"
ms.assetid: 79b0955a-5a86-46a8-90e9-4419c9068bbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии CLS CLS03411
В спецификации CLS разрешено только подмножество кодировок настраиваемых атрибутов.  
  
 В спецификации CLS разрешено только подмножество типов в качестве параметров конструктора настраиваемых атрибутов или в качестве типа членов данных настраиваемого атрибута. Возможны только следующие типы:  
  
-   System.Type  
  
-   System.String  
  
-   System.Char  
  
-   System.Boolean  
  
-   System.Byte  
  
-   System.Int16  
  
-   System.Int32  
  
-   System.Int64  
  
-   System.Single  
  
-   System.Double  
  
-   Любые типы перечисления, основанные на базовом целочисленном типе, совместимом с CLS  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS03411:  
  
```  
// CLS03411.cpp // compile with: /clr /LD // CLS03411 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; // CLS03411 [AttributeUsage(AttributeTargets::All, AllowMultiple=true)] public ref class MyAttribute1 : public Attribute { public: MyAttribute1(Object^ parameter) {} }; // OK [AttributeUsage(AttributeTargets::All, AllowMultiple=true)] public ref class MyAttribute3 : public Attribute { public: MyAttribute3(Char parameter) {} };  
```