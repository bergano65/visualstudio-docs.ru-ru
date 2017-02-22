---
title: "Функция SccRemove | Microsoft Docs"
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
  - "SccRemove"
helpviewer_keywords: 
  - "Функция SccRemove"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccRemove
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция удаляет файлы из системы управления версиями.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccRemove(  
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
 \[in\] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 \[in\] Массив имен файлов для удаления полный локальный путь.  
  
 lpComment  
 \[in\] Комментарий, применяемый к каждой удаления файла.  
  
 Возможности  
 \[in\] Команда флаги \(не используется\).  
  
 pvOptions  
 \[in\] Параметры конкретного подключаемого модуля системы управления версиями.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Удаление выполнено успешно.|  
|SCC\_E\_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC\_E\_OPNOTSUPPORTED|Система управления версиями не поддерживает эту операцию.|  
|SCC\_E\_ISCHECKEDOUT|Не удается удалить файл, так как пользователь в настоящее время он извлечен.|  
|SCC\_E\_ACCESSFAILURE|Произошла ошибка при доступе к системе управления версиями, вероятно, из\-за проблемы с сетью или конфликтов.|  
|SCC\_E\_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC\_E\_NONSPECIFICERROR|Неспецифическая ошибка; файл не был удален.|  
|SCC\_I\_OPERATIONCANCELED|Операция была отменена до завершения.|  
  
## Заметки  
 Эта функция удаляет файлы из системы управления версиями, но они не удаляются с локального жесткого диска пользователя.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)