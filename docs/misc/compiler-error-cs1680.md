---
title: "Ошибка компилятора CS1680 | Microsoft Docs"
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
  - "CS1680"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1680"
ms.assetid: 973da155-e6fa-4de8-94fd-7838f839a81f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1680
Недопустимый параметр псевдонима ссылки: "alias\=" — отсутствует имя файла  
  
 Эта ошибка происходит, когда вы используете атрибут `alias` с параметром компилятора **\/reference**, не указав допустимое имя файла.  
  
 При компиляции следующего примера возникнет ошибка CS1680.  
  
```  
// CS1680.cs // compile with: /reference:alias= // CS1680 expected // To resolve, specify the name of a file with an assembly manifest class MyClass {}  
  
```