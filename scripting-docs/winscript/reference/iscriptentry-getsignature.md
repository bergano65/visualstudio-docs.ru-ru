---
title: IScriptEntry::GetSignature | Документация Майкрософт
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
ms.openlocfilehash: 70cc1939ae4eb1e3c58d31b3d42b7f1b4603ce9e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145308"
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Задать сведения о типе с помощью [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) или [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Сведения о типе также может возникать с помощью операции, в зависимости от представления внутренней функции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)