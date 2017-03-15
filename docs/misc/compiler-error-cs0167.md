---
title: "Ошибка компилятора CS0167 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0167"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0167"
ms.assetid: e6901b40-11a0-422c-9ea3-3b25c0ad7791
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0167
В делегате "делегат" отсутствует метод Invoke  
  
 Вы импортировали и использовали управляемую программу \(использующую среду CLR .NET Framework\), созданную с помощью другого компилятора. Этот компилятор разрешил неправильно сформированный [делегат](/dotnet/csharp/language-reference/keywords/delegate). Таким образом, метод `Invoke` был недоступен. Дополнительные сведения см. в разделе [Делегаты](/dotnet/csharp/programming-guide/delegates/index).