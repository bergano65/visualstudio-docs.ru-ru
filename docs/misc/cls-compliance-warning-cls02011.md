---
title: "Предупреждение о соответствии спецификации CLS CLS02011 | Microsoft Docs"
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
  - "CLS02011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02011"
ms.assetid: 9466be1e-9558-49e8-9ea4-5cfc54a22066
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS02011
CLS\-совместимые классы, типы значений и интерфейсы должны реализовываться без интерфейсов, не соответствующих правилам CLS\-совместимости.  
  
 Тип, помеченный как CLS\-совместимый, имеет один или несколько базовых типов, которые не являются CLS\-совместимыми.  
  
 Дополнительные сведения о проверке CLS\-совместимости см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем примере возникает ошибка CLS02011:  
  
```  
// CLS02011.cpp // compile with: /clr /LD // CLS02011 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public interface class CompliantInterface {}; [CLSCompliant(false)] public interface class NotCompliantInterface {}; public ref class One : public NotCompliantInterface {};   // CLS02011 public ref class Two : public CompliantInterface {};   // OK  
```