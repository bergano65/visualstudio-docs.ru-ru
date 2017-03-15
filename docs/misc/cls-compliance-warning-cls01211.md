---
title: "Предупреждение о соответствии спецификации CLS CLS01211 | Microsoft Docs"
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
  - "CLS01211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01211"
ms.assetid: a6df4b7a-81e8-4e77-90d1-ec1cc3a759f5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS01211
Видимость и доступность типов и членов должна быть такой, чтобы типы в сигнатуре любого члена были видимы и доступны всегда, когда видим или доступен сам член. Например, тип, видимый за пределами его сборки, не должен иметь базовый тип, видимый только в пределах сборки.  
  
 Доступность типов и интерфейсов, наследуемых или реализуемых типом \(A\), должна быть не меньше доступности типа.  Например, открытый метод, видимый за пределами его сборки, не должен иметь аргументов, типы которых видимы только в пределах сборки.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS01211:  
  
```  
// CLS01211.cpp // compile with: /clr /LD // CLS01211 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private interface class I {}; public interface class I2 : public I {};  
```