---
title: "Функция SccGetExtendedCapabilities | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetExtendedCapabilities
helpviewer_keywords: SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 870d793a11cccdaae9657deabb0e3b08c4d8c6f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Функция get операция успешно завершена.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла ошибка с неизвестным или неопределенным.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается по запросу. то есть, при возможности необходимо проверить, этот метод вызывается для определения, поддерживается возможность. Указан только один флаг одновременно.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)   
 [Флаги возможностей](../extensibility/capability-flags.md)