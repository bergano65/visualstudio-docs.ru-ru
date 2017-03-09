---
title: "Предупреждение о соответствии CLS CLS01101 | Microsoft Docs"
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
  - "CLS01101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01101"
ms.assetid: 01034537-eee8-40e6-9139-d1788612738a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии CLS CLS01101
Все типы сигнатуры должны быть CLS\-совместимыми  
  
 Если тип является CLS\-совместимым, то все конструкторы в типе, если они не помечены как несовместимые с CLS, должны иметь CLS\-совместимые типы параметров.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
## Пример  
 При компиляции следующего примера будет выдано предупреждение CLS01101:  
  
```  
// CLS01101.cpp // compile with: /clr /LD // CLS01101 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; [CLSCompliant(true)] public ref class One { public: One(NotCompliantType^ parameter) {}   // CLS01101 One(CompliantType^ parameter) {}   // OK [CLSCompliant(false)] One(NotCompliantType^ param1, NotCompliantType^ param2) {}   // OK };  
```