---
title: "QUERYCHANGESFUNC | Microsoft Docs"
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
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "Функция обратного вызова QUERYCHANGESFUNC"
  - "Структура QUERYCHANGESDATA"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Это функция обратного вызова, используемые [SccQueryChanges](../extensibility/sccquerychanges-function.md) операцию перечислить коллекцию имен файлов и определить состояние каждого файла.  
  
 `SccQueryChanges` Получает список файлов и указатель на функцию `QUERYCHANGESFUNC` обратного вызова. Перечисляет заданный список подключаемый модуль системы управления версиями и предоставляет сведения о состоянии \(с помощью этой функции обратного вызова\) для каждого файла в списке.  
  
## Подпись  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## Параметры  
 pvCallerData  
 \[in\] `pvCallerData` Параметр, передаваемый в вызывающем объекте \(IDE\) [SccQueryChanges](../extensibility/sccquerychanges-function.md). Подключаемый модуль системы управления версиями следует делать никаких предположений относительно содержимого этого значения.  
  
 pChangesData  
 \[in\] Указатель на [Структура QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) структуры, описывающие изменения в файл.  
  
## Возвращаемое значение  
 IDE возвращает соответствующего кода ошибки:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Продолжайте обработку.|  
|SCC\_I\_OPERATIONCANCELED|Остановите обработку.|  
|SCC\_E\_xxx|Соответствующие ошибки SCC следует остановить обработку.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Структура QUERYCHANGESDATA  
 Структура, переданный для каждого файла выглядит следующим образом:  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 Размер этой структуры \(в байтах\).  
  
 lpFileName  
 Имя исходного файла для этого элемента.  
  
 dwChangeType  
 Код, указывающий состояние файла:  
  
|Код|Описание|  
|---------|--------------|  
|`SCC_CHANGE_UNKNOWN`|Невозможно определить, что изменилось.|  
|`SCC_CHANGE_UNCHANGED`|Имя этого файла не изменены.|  
|`SCC_CHANGE_DIFFERENT`|Файл с другим удостоверением, но тем же именем существует в базе данных.|  
|`SCC_CHANGE_NONEXISTENT`|Файл не существует в базе данных или локально.|  
|`SCC_CHANGE_DATABASE_DELETED`|Файл удален в базе данных.|  
|`SCC_CHANGE_LOCAL_DELETED`|Файл удален локально, но файл остается в базе данных. Если не удается определить, возвращают `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Файл добавлен в базу данных, но не существует локально.|  
|`SCC_CHANGE_LOCAL_ADDED`|Файл не существует в базе данных и новый локальный файл.|  
|`SCC_CHANGE_RENAMED_TO`|Файл переименован или перемещен в базе данных `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Файл переименован или перемещен в базу данных из `lpLatestName`; Если это слишком дорогими для отслеживания, возвращает другой флаг, например `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Текущее имя файла для этого элемента.  
  
## См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Коды ошибок](../extensibility/error-codes.md)