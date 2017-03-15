---
title: "Ошибка компилятора ресурсов RC2180 | Microsoft Docs"
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
  - "RC2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2180"
ms.assetid: 6d296138-7989-491e-a45b-6c3a4743116a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Ошибка компилятора ресурсов RC2180
не удается открыть временный файл  
  
 Компилятору ресурсов или Visual C\+\+ не удалось открыть временный файл. Вероятная причина заключается в том, что отсутствуют разрешения на запись в соответствующий каталог или что этот каталог не существует. Компилятор ресурсов или Visual C\+\+ пытается использовать файлы либо в каталоге, указанном в переменной среды **TMP**, либо в текущем каталоге, если каталог не задан.