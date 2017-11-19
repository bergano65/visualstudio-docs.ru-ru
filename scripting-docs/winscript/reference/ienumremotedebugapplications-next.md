---
title: "IEnumRemoteDebugApplications::Next | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplications.Next
apilocation: scrobj.dll
helpviewer_keywords: IEnumRemoteDebugApplications::Next
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13853bd0a35a9bce1217241b5675a22de386b7dd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationsnext"></a>IEnumRemoteDebugApplications::Next
`Next` Метод извлекает указанное число сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество сегментов для извлечения.  
  
 `ppda`  
 [out] Возвращает массив `IRemoteDebugApplication` интерфейсы, которые представляет извлекаемых сегменты.  
  
 `pceltFetched`  
 [out] Фактическое число сегментов, выбранных с помощью перечислителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод извлекает указанное число сегментов в последовательности перечисления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)