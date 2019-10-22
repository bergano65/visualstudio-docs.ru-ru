---
title: 'Иактивескриптстатс:: Ресетстатс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2767bb1e2cce3a11661ebaca37e66d33f95beb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577971"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
Сбрасывает статистику для этого скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод сбрасывает статистику для этого скрипта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)