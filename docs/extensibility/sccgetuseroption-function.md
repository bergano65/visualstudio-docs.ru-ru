---
title: "Функция SccGetUserOption | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetUserOption
helpviewer_keywords: SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd59cfada6064d40fe48df3cba4eaac3c3293b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
Эта функция извлекает множество параметров конкретного пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nOption  
 [in] Параметр, чтобы получить (см. примечания возможные параметры).  
  
 lpVal  
 [out] Значение, связанное с параметром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Параметр был успешно извлечен.|  
|SCC_E_OPNOTSUPPORTED|Параметр не поддерживается.|  
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Эта команда поддерживает следующие параметры:  
  
|Параметр User|Описание|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, является ли пользователь хочет извлекать локальную версию файлов. `lpVal`назначается `SCC_USEROPT_COLV_YES` (пользователю необходимо извлечь локальных файлов) или `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)