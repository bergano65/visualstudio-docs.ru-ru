---
title: Функция SccGetUserOption | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f73eff3f1be51045381c0eaa76d5d3914d8e9ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869272"
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
Эта функция получает различные параметры конкретного пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nOption  
 [in] Параметр, чтобы получить (см. в разделе "Примечания" для возможные варианты).  
  
 lpVal  
 [out] Значение, связанное с параметром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Параметр был успешно извлечен.|  
|SCC_E_OPNOTSUPPORTED|Параметр не поддерживается.|  
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Эта команда поддерживает следующие параметры:  
  
|Параметр User|Описание|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, хочет ли пользователь извлечь локальную версию файлов. `lpVal` назначается `SCC_USEROPT_COLV_YES` (пользователю нужно извлечь локальных файлов) или `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)