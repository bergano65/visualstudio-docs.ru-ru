---
title: "Ошибка компилятора CS2021 | Microsoft Docs"
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
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS2021
Слишком длинное или недопустимое имя файла "файл"  
  
 Длина всех имен файлов, передаваемых компилятору C\#, не должна превышать значение `_MAX_PATH` \(определенное в файле заголовка Windows\). Компилятор выдает эту ошибку в указанных ниже ситуациях.  
  
-   Имя файла \(включая путь\) длиннее, чем `_MAX_PATH`.  
  
-   Имя файла содержит недопустимые символы.  
  
-   Имя файла содержит подстановочные знаки там, где это недопустимо \(например, в именах файлов ресурсов\).