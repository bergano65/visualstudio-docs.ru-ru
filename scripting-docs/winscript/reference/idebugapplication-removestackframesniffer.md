---
title: "IDebugApplication::RemoveStackFrameSniffer | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11289972dbd39d2e6221fb223a0d933ed90589c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Удаляет поставщик перечислитель кадра стека из этого приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCookie`  
 [in] Файл cookie, возвращаемые `AddStackFrameSniffer` метод при добавлении поставщика перечислитель кадра стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `RemoveStackFrameSniffer` Метод удаляет поставщик перечислитель кадра стека из этого приложения.  
  
## <a name="see-also"></a>См. также  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)