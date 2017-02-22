---
title: "Отчетные функции-ловушки | Microsoft Docs"
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
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgReport - функция"
  - "_CrtSetReportHook - функция"
  - "отладчик, функции ловушек отчетов"
  - "отладка [C++], функции ловушек"
  - "ловушки, отчет"
  - "выделение памяти, куча отладки"
  - "функции ловушек отчетов"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Отчетные функции-ловушки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отчетные функции\-ловушки, установленные с помощью [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook), вызываются каждый раз при создании отчета отладки [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw).  Помимо всего прочего их можно использовать для фильтрации отчетов, которые позволяют отобрать выделения конкретного типа.  Отчетная функция\-ловушка должна иметь следующий прототип:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Указатель, передаваемый **\_CrtSetReportHook**, имеет тип **\_CRT\_REPORT\_HOOK**, как определено в CRTDBG.H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Когда CRT вызывает функцию\-ловушку, аргумент *nRptType* содержит категорию отчета \(**\_CRT\_WARN**, **\_CRT\_ERROR** или **\_CRT\_ASSERT**\), *szMsg* содержит указатель на полностью собранную строку отчетного сообщения, а *retVal* задает значение, определяющее поведение `_CrtDbgReport`, который может продолжить обычное выполнение после создания отчета или запустить отладчик. \(Значение *retVal*, равное нулю, позволяет продолжить выполнение, а значение 1 запускает отладчик.\)  
  
 Если ловушка полностью обрабатывает сообщение и дальнейшая выдача отчета не требуется, она возвращает значение **TRUE**.  Если возвращается значение **FALSE**, `_CrtDbgReport` будет дальше выдавать отчетные сообщения в обычном режиме.  
  
## См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/ru-ru/21e1346a-6a17-4f57-b275-c76813089167)