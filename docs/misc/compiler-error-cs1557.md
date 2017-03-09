---
title: "Ошибка компилятора CS1557 | Microsoft Docs"
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
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1557
Класс "класс" не может использоваться для метода Main, так как находится в другом выходном файле  
  
 Параметр компилятора [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) был указан для одного выходного файла в компиляции с несколькими выходными файлами. Однако класс не найден в исходном коде для компиляции с параметром \/main; он найден в исходном коде для одного из других выходных файлов компиляции.