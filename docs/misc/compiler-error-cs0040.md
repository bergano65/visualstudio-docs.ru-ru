---
title: "Ошибка компилятора CS0040 | Microsoft Docs"
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
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0040
Непредвиденная ошибка при создании файла отладочной информации — "причина"  
  
 Эта ошибка может возникнуть при использовании параметра компилятора [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) и указывает, что компилятору не удалось выполнить запись в PDB\-файл. Возможные способы устранения этой ошибки включают переустановку Visual Studio, проверку наличия у компилятора доступа на запись в файл или каталог или отказ от компиляции с параметром \/debug.