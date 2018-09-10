---
title: IActiveScriptProfilerControl::StartProfiling | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5540573991be11230acb33b088174bbb5c39f7f7
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281720"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Запускает профилирование на обработчик скриптов. Обработчик скриптов создает экземпляр объекта профилировщика с помощью вызова [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Параметры  
 `clsidProfilerObject`  
 [in] Идентификатор (CLSID) объекта профилировщика создаваемого класса.  
  
 `dwEventMask`  
 [in] 4-байтовое Битовая маска, указывающее типы событий. Определенные биты в [перечисление PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] 4-байтовое значение, передаваемое объект профилировщика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Профилирование уже включено.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)