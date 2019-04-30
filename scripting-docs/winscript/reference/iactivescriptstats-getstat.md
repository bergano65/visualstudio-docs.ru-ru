---
title: IActiveScriptStats::GetStat | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8befb3da4e4b6f060a5f58aedec3604afe70aefb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992013"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Возвращает одно из стандартных внести в скрипт статистику.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stid`  
 [in] Указывает, какой статистики для возврата. Должен иметь значение:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Возвращает число инструкций, поскольку в сценарий, запущенный или сброса статистики.|  
  
 `pluHi`  
 [out] Старшие 32 разряда 64-разрядного целого числа без знака, представляющее статистику.  
  
 `pluLo`  
 [out] Младшие 32 разряда 64-разрядного целого числа без знака, представляющее статистику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Возможные значения включают, но не ограничиваются значения в таблице ниже.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает одно из стандартных внести в скрипт статистику.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)