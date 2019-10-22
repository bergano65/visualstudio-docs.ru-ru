---
title: 'IScriptEntry:: Signature | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575421"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Возвращает сведения о типе для объекта `IScriptEntry` функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppti`  
 заполняет Введите сведения, связанные с этим объектом `IScriptEntry` функции.  
  
 `piMethod`  
 заполняет Индекс метода в объекте `ITypeInfo`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Сведения о типе задаются с помощью [IScriptEntry:: сетсигнатуре](../../winscript/reference/iscriptentry-setsignature.md) или [Искриптноде:: креатечилдхандлер](../../winscript/reference/iscriptnode-createchildhandler.md). Сведения о типе также могут создаваться записью на основе внутреннего представления функции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)