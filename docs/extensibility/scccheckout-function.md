---
title: "Функция SccCheckout | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckout"
helpviewer_keywords: 
  - "Функция SccCheckout"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccCheckout
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Получает список имен полным путем к файлу, эта функция извлекает их на локальном диске. Для извлечения всех файлов относится комментарий. Комментарий может быть `null` строку.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Параметры  
 pvContext  
 \[in\] Структура подключаемого модуля контекста исходного элемента управления.  
  
 hWnd  
 \[in\] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 nFiles  
 \[in\] Число файлов, выбранных для извлечения.  
  
 lpFileNames  
 \[in\] Массив имен файлов для извлечения полный локальный путь.  
  
 lpComment  
 \[in\] Комментарий, применяемый к каждой из выбранных извлекаемых файлов.  
  
 Возможности  
 \[in\] Команда флагов \(см. [Битовые флаги, используемые команды](../extensibility/bitflags-used-by-specific-commands.md)\).  
  
 pvOptions  
 \[in\] Параметры конкретного подключаемого модуля системы управления версиями.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Извлечение выполнена успешно.|  
|SCC\_E\_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC\_E\_ACCESSFAILURE|Произошла ошибка при доступе к системе управления версиями, вероятно, из\-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC\_E\_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC\_E\_NONSPECIFICERROR|Неспецифическая ошибка. Файл не был извлечен.|  
|SCC\_E\_ALREADYCHECKEDOUT|Пользователь уже извлек файл.|  
|SCC\_E\_FILEISLOCKED|Файл заблокирован Запрет создания новых версий.|  
|SCC\_E\_FILEOUTEXCLUSIVE|Другой пользователь выполнит монопольного извлечения на этот файл.|  
|SCC\_I\_OPERATIONCANCELED|Операция была отменена до завершения.|  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые команды](../extensibility/bitflags-used-by-specific-commands.md)