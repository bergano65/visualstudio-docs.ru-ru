---
title: IScriptEntry::GetRange | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729044"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Возвращает начальную позицию и длину запись.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pichMin`  
 [out] Для `IScriptEntry` объектов, которые задают блок скрипта возвращает 0.  
  
 Для `IScriptEntry` объектов, которые задают объект функции возвращает начальную позицию функции в текущем блоке скрипта.  
  
 Для `IScriptScriptlet` объектов, возвращается 0.  
  
 `pcch`  
 [out] Для `IScriptEntry` объектов, которые задают блок скрипта возвращает длину текста.  
  
 Для `IScriptEntry` объектов, которые задают объект функции возвращает длину определения функции.  
  
 Для `IScriptScriptlet` , возвращает длину записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)