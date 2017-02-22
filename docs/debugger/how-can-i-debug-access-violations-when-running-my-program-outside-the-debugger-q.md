---
title: "Как отладить нарушения доступа при запуске программы без отладчика? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "отладка нарушений доступа"
  - "отладка [Visual Studio], нарушения доступа"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Как отладить нарушения доступа при запуске программы без отладчика?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Описание проблемы  
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа.  Как это отладить?  
  
## Решение  
 Активируйте параметр [JIT\-отладка](../debugger/just-in-time-debugging-in-visual-studio.md) и запустите автономное выполнение программы до момента возникновения нарушения доступа.  Затем в диалоговом окне **Нарушение доступа** можно нажать **Отмена** и запустить отладчик.  
  
 Кроме того, обратитесь к статье Q133174 информационной базы данных, "How to Locate Where a General Protection \(GP\) Fault Occurs". Статьи базы знаний можно найти на компакт\-диске библиотеки MSDN или на веб\-сайте [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)