---
title: Функция SccGetExtendedCapabilities | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46ae3e051028e8239be5949500ebb710d67eee17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137220"
---
# <a name="sccgetextendedcapabilities-function"></a>Функция SccGetExtendedCapabilities
Эта функция возвращает дополнительные возможности, поддерживаемые подключаемый модуль системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 lSccExCaps  
 [in] Флаг, указывающий расширенные возможности, для которой требуется проверить (см. в таблице расширенных возможностей кода [флаги возможностей](../extensibility/capability-flags.md) для флаги).  
  
 pbSupported  
 [out] Возвращает ненулевое значение (`TRUE`) поддерживается возможностями указанного; в противном случае возвращает ноль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Функция get операция успешно завершена.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла ошибка с неизвестным или неопределенным.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается по запросу. то есть, при возможности необходимо проверить, этот метод вызывается для определения, поддерживается возможность. Указан только один флаг одновременно.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)   
 [Флаги возможностей](../extensibility/capability-flags.md)