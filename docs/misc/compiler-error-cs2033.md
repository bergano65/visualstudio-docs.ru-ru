---
title: "Ошибка компилятора CS2033 | Microsoft Docs"
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
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS2033
Невозможно создать короткое имя файла "имя\_файла", когда уже существует длинное имя файла с аналогичным коротким именем файла  
  
 Скомпилируйте какой\-либо файл C\# с именем длиннее восьми символов. Затем скомпилируйте другой файл с коротким вариантом предыдущего имени файла, таким как первые шесть символов имени плюс "~1". Во время второй компиляции возникнет данная ошибка.  
  
 Чтобы устранить эту ошибку, укажите такие короткие имена файлов, которые не конфликтуют с длинными именами.