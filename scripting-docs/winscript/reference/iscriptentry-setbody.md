---
title: IScriptEntry::SetBody | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06ee232aa730366e9a23e15cdc45f6734b9ef744
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729144"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Задает текст, который находится в теле `IScriptEntry` блок сценария или `IScriptScriptlet` сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 [in] Для `IScriptEntry` блок скрипта, `psz` — это текст, заключенный в теги сценариев.  
  
 Для `IScriptEntry` блока function `psz` представляет собой тело функции.  
  
 Для `IScriptScriptlet` объекта (который является производным от `IScriptEntry`), `psz` текст сценария сценариев.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)