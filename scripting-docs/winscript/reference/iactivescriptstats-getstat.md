---
title: 'Иактивескриптстатс:: stat | Документация Майкрософт'
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
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574338"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Возвращает одну из стандартных статистических данных скрипта.  
  
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
 окне Указывает, какую статистику следует вернуть. Значение должно быть равно:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Возвращает количество инструкций, выполненных с момента запуска скрипта или сброса статистики.|  
  
 `pluHi`  
 заполняет Старшие 32 бит 64-разрядного целого числа без знака, представляющего статистику.  
  
 `pluLo`  
 заполняет Младший 32 бит 64-разрядного целого числа без знака, представляющего статистику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Возможные значения включают, но не ограничиваются значениями, приведенными в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает одну из стандартных статистических данных скрипта.  
  
## <a name="see-also"></a>См. также  
 [Иактивескриптстатс:: жетстатекс](../../winscript/reference/iactivescriptstats-getstatex.md)    
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)