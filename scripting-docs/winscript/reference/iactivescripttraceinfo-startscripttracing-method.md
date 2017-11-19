---
title: "Метод IActiveScriptTraceInfo::StartScriptTracing | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e999ad0d40f4d832330fee6db17b64ae9da50f08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>Метод IActiveScriptTraceInfo::StartScriptTracing
Запускает трассировку сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Параметры  
 `pSiteTraceInfo`  
 Указатель на IActiveScriptSiteTraceInfo поставщика услуг размещения.  
  
 `guidContextId`  
 Идентификатор GUID контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Ниже перечислены возможные возвращаемые значения для этого метода.  
  
1.  Значение S_OK: успех.  
  
2.  E_POINTER: `pSiteTraceInfo` является указателем NULL.  
  
3.  Значение E_NOTIMPL: Не реализовано.