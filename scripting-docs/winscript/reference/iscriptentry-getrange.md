---
title: IScriptEntry::GetRange | Документация Майкрософт
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
ms.openlocfilehash: 7baa284be4fa7f45f247df7f4b3d140869f254b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787741"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Возвращает начальное положение и длину запись.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pichMin`  
 [out] Для `IScriptEntry` объектов, указывающих блок скрипта возвращает 0.  
  
 Для `IScriptEntry` объектов, указывающих объект функции возвращает начальное положение функции в текущем блоке скрипта.  
  
 Для `IScriptScriptlet` , возвращает 0.  
  
 `pcch`  
 [out] Для `IScriptEntry` объектов, указывающих блок скрипта возвращает длину текста.  
  
 Для `IScriptEntry` объектов, указывающих объект функции возвращает длину определения функции.  
  
 Для `IScriptScriptlet` , возвращает длину вводимой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)