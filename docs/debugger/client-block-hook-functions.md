---
title: "Функции-ловушки клиентского блока | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtSetDumpClient - функция"
  - "клиентские блоки, функции ловушек"
  - "клиентские блоки, проверка и отчеты о данных"
  - "отладка [C++], функции ловушек"
  - "ловушки, клиентский блок"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Функции-ловушки клиентского блока
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если нужно проверить или вывести данные, хранящиеся в блоках типа `_CLIENT_BLOCK`, можно написать для этого специальную функцию.  Эта функция должна иметь прототип наподобие следующего, определенного в CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Другими словами, функция\-ловушка должна принимать указатель типа **void** на начало блока выделения и значение типа **size\_t**, показывающее размер выделения, и возвращать тип `void`.  Все остальное задается по желанию.  
  
 Один раз установленная с помощью[\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient), функция\-ловушка будет вызываться всякий раз при дампе блока `_CLIENT_BLOCK`.  [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) можно применять для получения сведений о типе или подтипе выводимых блоков.  
  
 Указатель на функцию, который передается `_CrtSetDumpClient`, имеет тип **\_CRT\_DUMP\_CLIENT**, как определено в CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/ru-ru/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)