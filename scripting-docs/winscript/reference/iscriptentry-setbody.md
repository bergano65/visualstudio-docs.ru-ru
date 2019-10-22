---
title: 'IScriptEntry:: Сетбоди | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575380"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Задает текст, который находится в теле блока `IScriptEntry` скрипта или `IScriptScriptlet` скриптлет.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 окне Для `IScriptEntry` блока сценария `psz` — это текст, заключенный в теги script.  
  
 Для `IScriptEntry` блока функции `psz` является телом функции.  
  
 Для объекта `IScriptScriptlet` (который является производным от `IScriptEntry`) `psz` является текстом скрипта скриптлет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)