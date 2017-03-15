---
title: "Предупреждение о соответствии спецификации CLS CLS01601 | Microsoft Docs"
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
  - "CLS01601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01601"
ms.assetid: fa162fc6-a0fd-4a0f-a201-4f166304d057
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01601
Элементы массива должны быть CLS\-совместимого типа, а измерения массива иметь нижнюю границу, равную нулю  
  
 Элементы массива должны быть CLS\-совместимого типа, а измерения массива иметь нижнюю границу, равную нулю. Для различения перегрузок достаточно, чтобы элемент был массивом и у него был задан тип элементов. Если перегрузка основана на нескольких типах массивов, типы элементов должны быть именованными.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS01601:  
  
```  
// CLS01601.cpp // compile with: /clr /LD // CLS01601 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01601 One(array<NotCompliantType^>^ param) {} // OK One(array<CompliantType^>^ param) {} };  
```