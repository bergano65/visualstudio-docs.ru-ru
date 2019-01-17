---
title: IScriptEntry::GetSignature | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 245b5806006ad94740e09e23f881e26e071a3bc1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092733"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Возвращает сведения о типе для `IScriptEntry` объект функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppti`  
 [out] Введите сведения, связанные с этим `IScriptEntry` объект функции.  
  
 `piMethod`  
 [out] Метод index в `ITypeInfo` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Задать сведения о типе с помощью [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) или [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Сведения о типе также может возникать с помощью операции, в зависимости от представления внутренней функции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)