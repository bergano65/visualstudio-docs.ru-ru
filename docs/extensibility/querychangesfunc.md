---
title: QUERYCHANGESFUNC | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1df5f21ffed27c45ebee6315fcc29ee1dcc8fa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139813"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Функция обратного вызова, используемые [SccQueryChanges](../extensibility/sccquerychanges-function.md) операции для перечисления коллекцию имен файлов и определить состояние каждого файла.  
  
 `SccQueryChanges` Получает список файлов и указатель на функцию `QUERYCHANGESFUNC` обратного вызова. Подключаемый модуль системы управления версиями Перечисляет заданный список и состояние (через этот обратный вызов) для каждого файла в списке.  
  
## <a name="signature"></a>Подпись  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Параметры  
 pvCallerData  
 [in] `pvCallerData` Параметр, передаваемый в вызывающем объекте (IDE) [SccQueryChanges](../extensibility/sccquerychanges-function.md). Подключаемый модуль системы управления версиями следует делать никаких предположений относительно содержимого этого значения.  
  
 pChangesData  
 [in] Указатель на [QUERYCHANGESDATA структуры](#LinkQUERYCHANGESDATA) структуры, описывающие изменения в файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Интегрированная среда разработки возвращается код соответствующее сообщение об ошибке:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Продолжайте обработку.|  
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|  
|SCC_E_xxx|Любые соответствующие ошибки SCC следует остановить обработку.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Структура QUERYCHANGESDATA  
 Структура, переданный для каждого файла выглядит следующим образом:  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 Размер этой структуры (в байтах).  
  
 lpFileName  
 Исходное имя файла для этого элемента.  
  
 dwChangeType  
 Код, указывающий состояние файла:  
  
|Код|Описание|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Невозможно определить, какие изменения были внесены.|  
|`SCC_CHANGE_UNCHANGED`|Имя этого файла не изменены.|  
|`SCC_CHANGE_DIFFERENT`|Файл с другим удостоверением, но тем же именем существует в базе данных.|  
|`SCC_CHANGE_NONEXISTENT`|Файл не существует в базе данных или локально.|  
|`SCC_CHANGE_DATABASE_DELETED`|Файл удален в базе данных.|  
|`SCC_CHANGE_LOCAL_DELETED`|Файл удален локально, но файл все еще существует в базе данных. Если не удается определить, возвращают `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Файл добавлен в базу данных, но не существует локально.|  
|`SCC_CHANGE_LOCAL_ADDED`|Файл не существует в базе данных и новый локальный файл.|  
|`SCC_CHANGE_RENAMED_TO`|Файл переименован или перемещен в базе данных как `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Файл переименован или перемещен в базу данных из `lpLatestName`; Если это слишком затратными для отслеживания, возвращают различные флаг, такими как `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Текущее имя файла для этого элемента.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Коды ошибок](../extensibility/error-codes.md)