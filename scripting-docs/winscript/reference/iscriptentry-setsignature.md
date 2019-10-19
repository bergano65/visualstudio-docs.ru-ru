---
title: 'IScriptEntry:: Сетсигнатуре | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575342"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Задает сведения о типе для объекта `IScriptEntry` функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pti`  
 окне Сведения о типе.  
  
 `iMethod`  
 окне Индекс метода в объекте `ITypeInfo`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Сведения о типе задаются с помощью `IScriptEntry::SetSignature` или [искриптноде:: креатечилдхандлер](../../winscript/reference/iscriptnode-createchildhandler.md). Сведения о типе также могут создаваться записью на основе внутреннего представления функции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)