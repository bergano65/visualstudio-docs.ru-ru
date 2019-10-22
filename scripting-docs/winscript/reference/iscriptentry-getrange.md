---
title: 'IScriptEntry:: Range | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575435"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Возвращает начальную и длину записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pichMin`  
 заполняет Для `IScriptEntry` объектов, указывающих блок скрипта, возвращает значение 0.  
  
 Для `IScriptEntry` объектов, указывающих объект функции, возвращает начальную точку функции в текущем блоке скрипта.  
  
 Для `IScriptScriptlet` объектов возвращает 0.  
  
 `pcch`  
 заполняет Для `IScriptEntry` объектов, указывающих блок скрипта, возвращает длину текста.  
  
 Для `IScriptEntry` объектов, указывающих объект функции, возвращает длину определения функции.  
  
 Для `IScriptScriptlet` объектов возвращает длину записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)