---
title: "Предупреждение компилятора ресурсов RC4204 | Microsoft Docs"
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
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение компилятора ресурсов RC4204
Символ ASCII не соответствует виртуальному коду клавиши.  
  
 Строковый литерал был использован для виртуального кода клавиши в акселераторе VIRTKEY.  
  
 Это предупреждение позволяет продолжить работу, но имейте в виду, что созданные сочетания клавиш могут не соответствовать указанной строке. \(акселераторы VIRTKEY используют другие коды клавиш, чем акселераторы ASCII\).  
  
 Если строковые литералы являются синтаксически правильными, вы можете только обеспечить получение нужных сочетаний клавиш с помощью значений **VK\_\*** `#define` в WINDOWS.h.