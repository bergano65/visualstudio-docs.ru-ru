---
title: "IDebugSessionProviderEx:CanJITDebug | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSessionProviderEx:CanJITDebug
apilocation: scrobj.dll
ms.assetid: 68f91bed-ca69-46b5-b517-ca9ca80b8803
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd2f9245f6691b2faaae75e064a299a22c59255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderexcanjitdebug"></a>IDebugSessionProviderEx:CanJITDebug
Определяет, можно ли указанный процесс отладки с отладкой только в момент времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CanJITDebug(  
   DWORD  pid  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pid`  
 [in] Идентификатор процесса для отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)