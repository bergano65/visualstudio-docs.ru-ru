---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01e55d793d174f550e33e18558eccc19d417c80b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993094"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Задает битовую маску 4 байтам, указывающее типы событий, которые должны вызываться обработчиком сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwEventMask`  
 [in] 4-байтовое Битовая маска, указывающее типы событий. Определенные биты в [перечисление PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)