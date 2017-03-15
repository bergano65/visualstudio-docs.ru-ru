---
title: "Предупреждение о соответствии спецификации CLS CLS00500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS00500
Все имена в CLS\-совместимой области должны быть разными независимо от типа.  
  
 Все имена, которые вводятся в CLS\-совместимой области, должны быть различными независимо от типа, кроме случаев, когда имена одинаковы и разрешаются посредством перегрузки. В рамках CLS два имени считаются одинаковыми, если совпадают их записи в нижнем регистре. Перегружать можно только свойства и методы. Свойства и методы должны перегружаться только на основе количества и типов их параметров, за исключением операторов преобразования, которые также могут перегружаться на основе их типа возврата; дополнительные сведения см. в разделе [Заданные пользователем преобразования](/visual-cpp/dotnet/user-defined-conversions-cpp-cli).  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Следующий пример приводит к возникновению предупреждения CLS00500:  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```