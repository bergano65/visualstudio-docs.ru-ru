---
title: "Ошибка компилятора CS1541 | Microsoft Docs"
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
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1541
Недопустимый параметр ссылки: "символ" — ссылки на каталоги невозможны  
  
 Компилятор обнаружил попытку указания каталога вместо конкретного файла. Например, при использовании параметра компилятора [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) необходимо указать файл; каталог указывать нельзя.  
  
 Например, ошибка CS1541 может быть вызвана передачей компилятору параметра `/reference:c:\`.