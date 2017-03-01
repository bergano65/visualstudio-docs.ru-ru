---
title: "Функция SccGetExtendedCapabilities | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c0331979eaae065730dab5d5daf0e226844d5e7a
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetextendedcapabilities-function"></a>Функция SccGetExtendedCapabilities
Эта функция возвращает дополнительные возможности, поддерживаемые подключаемым модулем системы управления версиями.  
  
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
 [in] Флаг, указывающий, расширенные возможности для тестирования (см. в таблице расширенных возможностей кода [флаги возможностей](../extensibility/capability-flags.md) для флаги).  
  
 pbSupported  
 [out] Возвращает ненулевое значение (`TRUE`) определенные возможности поддерживается; в противном случае — возвращает ноль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Возможность получения операция успешно завершена.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла ошибка с неизвестным или неопределенным.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается по запросу. то есть, когда функция должна быть проверена, этот метод вызывается для определения, поддерживается возможность. Указан только один флаг одновременно.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)   
 [Флаги возможностей](../extensibility/capability-flags.md)
