---
title: IActiveScriptStats::GetStat | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725234"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Возвращает стандартный сценарий статистики.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
|SCRIPTSTAT_STATEMENT_COUNT|1|Возвращает число инструкций, выполненных с момента запуска скрипта или сброса статистики.|  
  
 `pluHi`  
 [out] Старшие 32 разряда 64-разрядное целое число без знака, представляющее статистику.  
  
 `pluLo`  
 [out] Младшие 32 разряда 64-разрядное целое число без знака, представляющее статистику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются значениями в таблице ниже.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает статистики стандартного скрипта.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)