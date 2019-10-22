---
title: 'Идебугхелпер:: Креатесимплеконнектионпоинт | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06324b0d10eb6d0d69b6426276d5df7f382d2abe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562454"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Возвращает интерфейс события, который заключает в оболочку заданный объект `IDispatch`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdisp`  
 окне Объект `IDispatch` для переноса.  
  
 `ppscp`  
 заполняет Интерфейс событий, который служит оболочкой для `pdisp`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Возвращает интерфейс события, который упаковывает заданный `IDispatch` (см. [интерфейс исимплеконнектионпоинт](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугхелпер](../../winscript/reference/idebughelper-interface.md)  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)