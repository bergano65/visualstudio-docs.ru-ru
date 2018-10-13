---
title: Функция SccGetExtendedCapabilities | Документация Майкрософт
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
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03476339f4cf70f572bc76c90f9919dd3513df17
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181029"
---
# <a name="sccgetextendedcapabilities-function"></a>Функция SccGetExtendedCapabilities
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [in] Флаг, указывающий функцию расширенной, для которого нужно проверить (см. в таблице расширенные возможности кода в [флаги возможностей](../extensibility/capability-flags.md) для флаги).  
  
 pbSupported  
 [out] Возвращает ненулевое значение (`TRUE`) Если указанная возможность поддерживается; в противном случае возвращает 0 (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Операция получения возможностей, успешно завершена.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла ошибка неизвестен или не задан.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается по запросу; то есть, при возможности должна быть проверена, этот метод вызывается для определения, поддерживается возможность. Указывается только один флаг за раз.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)   
 [Флаги возможностей](../extensibility/capability-flags.md)

