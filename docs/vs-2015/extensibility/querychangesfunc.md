---
title: QUERYCHANGESFUNC | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9a0bbf3c26f797ec1bbf67ad8439e5f5ba05b11
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764210"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это функция обратного вызова, используемые [SccQueryChanges](../extensibility/sccquerychanges-function.md) операцию, чтобы перечислить коллекцию имен файлов и определить состояние каждого файла.  
  
 `SccQueryChanges` Функции приводится список файлов и указатель на `QUERYCHANGESFUNC` обратного вызова. Подключаемый модуль системы управления версиями перечисляет для данного списка и предоставляет статус (с помощью этой функции обратного вызова) для каждого файла в списке.  
  
## <a name="signature"></a>Подпись  
  
```cpp#  
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
 Интегрированная среда разработки возвращает код соответствующее сообщение об ошибке:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Продолжайте обработку.|  
|SCC_I_OPERATIONCANCELED|Остановите обработку.|  
|SCC_E_xxx|Любой соответствующее сообщение об ошибке SCC следует остановить обработку.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Структура QUERYCHANGESDATA  
 Структуры, переданной в для каждого файла выглядит следующим образом:  
  
```cpp#  
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
  
|Код|Описание:|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Не удается определить, какие изменения были внесены.|  
|`SCC_CHANGE_UNCHANGED`|Имя этого файла не изменены.|  
|`SCC_CHANGE_DIFFERENT`|Файл с идентификатором, но тем же именем существует в базе данных.|  
|`SCC_CHANGE_NONEXISTENT`|Файл не существует в базе данных или локально.|  
|`SCC_CHANGE_DATABASE_DELETED`|Файл удален в базе данных.|  
|`SCC_CHANGE_LOCAL_DELETED`|Файл удален локально, но файл по-прежнему существует в базе данных. Если это не может быть определено, возвращается `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Файл добавлен в базу данных, но не существует локально.|  
|`SCC_CHANGE_LOCAL_ADDED`|Файл не существует в базе данных и представляет собой новый локальный файл.|  
|`SCC_CHANGE_RENAMED_TO`|Файл переименован или перемещен в базе данных как `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Файл переименован или перемещен в базе данных на `lpLatestName`; Если это слишком дорого отслеживать, возвращает другой флаг, например `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Текущее имя файла для этого элемента.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализованные интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Коды ошибок](../extensibility/error-codes.md)

