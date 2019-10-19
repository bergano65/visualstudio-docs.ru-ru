---
title: 'IRemoteDebugApplicationEvents:: Онсетнаме | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnSetName
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnSetName
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb2d3b301888015c2815725c5d1c7903758e319a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571932"
---
# <a name="iremotedebugapplicationeventsonsetname"></a>IRemoteDebugApplicationEvents::OnSetName
Обрабатывает событие имени набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrName`  
 окне Новое имя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод обрабатывает событие присвоения имени.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)