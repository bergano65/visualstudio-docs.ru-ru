---
title: "Как определить, повреждают ли указатели адрес памяти? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "адреса, указатели адресов повреждения памяти"
  - "адрес повреждения памяти"
  - "отладка [C++], повреждение памяти"
  - "повреждение адресации памяти с помощью указателей"
  - "память, повреждение"
  - "указатели, адреса повреждений памяти"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Как определить, повреждают ли указатели адрес памяти?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Описание проблемы  
 Возможно, один из указателей повреждает память по адресу 0x00408000.  Как определить, что происходит в этой точке?  
  
## Решение  
  
#### Проверка целостности кучи  
  
-   В большинстве случаев повреждение памяти происходит из\-за повреждения кучи.  Используйте программу глобальных флагов \(gflags.exe\) или pageheap.exe.  Подробнее см. на странице [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;ru\-ru;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### Поиск места изменения адреса памяти  
  
1.  Задайте точку останова данных по адресу 0x00408000.  Подробнее см. раздел [Установка точки останова, действующей при изменении данных \(только для машинного кода C\+\+\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_).  
  
2.  При попадании в точку останова используйте окно **Память** для просмотра содержимого памяти начиная с адреса 0x00408000.  Дополнительные сведения см. в разделе [Окно памяти](../debugger/memory-windows.md).  
  
## См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)