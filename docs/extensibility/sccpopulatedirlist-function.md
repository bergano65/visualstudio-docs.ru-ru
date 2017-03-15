---
title: "Функция SccPopulateDirList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "Функция SccPopulateDirList"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Функция SccPopulateDirList
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция определяет, какие каталоги и \(при необходимости\) файлы хранятся в системе управления версиями, такой же список каталогов для проверки.  
  
## Синтаксис  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### Параметры  
 pContext  
 \[in\] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nDirs  
 \[in\] Количество путей к каталогам в `lpDirPaths` массива.  
  
 lpDirPaths  
 \[in\] Массив путей к каталогам для проверки.  
  
 pfnPopulate  
 \[in\] Функция обратного вызова для каждого путь к каталогу и \(необязательно\) имя файла в `lpDirPaths` \(в разделе [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Подробные сведения\).  
  
 pvCallerData  
 \[in\] Без изменений значение, передаваемое функции обратного вызова.  
  
 Возможности  
 \[in\] Сочетание значений, определяющих, как обрабатываются каталоги \(в разделе «Флаги PopulateDirList» [Битовые флаги, используемые команды](../extensibility/bitflags-used-by-specific-commands.md) Возможные значения\).  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Операция успешно завершена.|  
|SCC\_E\_UNKNOWNERROR|Произошла ошибка.|  
  
## Заметки  
 Функции обратного вызова передаются только те каталоги и \(необязательно\) имена файлов, которые расположены в репозитории системы управления версиями.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [Битовые флаги, используемые команды](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Коды ошибок](../extensibility/error-codes.md)