---
title: Функция SccBackgroundGet | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9ac53809a5735457d7604593e975bb764bbdf81
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639091"
---
# <a name="sccbackgroundget-function"></a>Функция SccBackgroundGet
Эта функция извлекает из системы управления версиями каждого из указанных файлов без участия пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 [in, out] Массив имен файлов, которые требуется получить.  
  
> [!NOTE]
>  Имена должны быть полное локальные имена файлов.  
  
 dwFlags  
 [in] Команда флаги (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Уникальное значение, связанное с данной операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Операция успешно завершена.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Получение фона уже выполняется (подключаемый модуль системы управления версиями вы получите это только в том случае, если он не поддерживает одновременное пакетных операций).|  
|SCC_I_OPERATIONCANCELED|Операция была отменена, прежде чем завершить.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция всегда вызывается в потоке, отличном от того, в который загружен модуль управления версиями. Эта функция не должен возвращать до его завершения; Тем не менее он может вызываться несколько раз с нескольких списков файлов, для всех, в то же время.  
  
 Использование `dwFlags` аргумент совпадает со значением [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)