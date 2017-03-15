---
title: "Ошибка компилятора CS1562 | Microsoft Docs"
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
  - "CS1562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1562"
ms.assetid: fbadbcc6-9cf2-4af6-b372-fd4e4da4402e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1562
Для создания результирующего файла без исходных текстов должен быть задан параметр \/out.  
  
 Компиляция может создать выходной файл, но отсутствовал входной файл исходного кода, из которого можно было бы вывести имя выходного файла. Например, вы могли пытаться компилировать файл только метаданных или только ресурсов.  
  
 Для задания имени выходного файла используйте параметр компилятора [\/out](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).