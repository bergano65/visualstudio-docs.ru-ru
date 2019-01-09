---
title: IScriptEntry::SetSignature | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 660f667d3542ff2cb9a7e96444d98b3082218a2a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089509"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Задает сведения о типе для `IScriptEntry` объект функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pti`  
 [in] Сведения о типе.  
  
 `iMethod`  
 [in] Индекс в метод `ITypeInfo` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Задать сведения о типе с помощью `IScriptEntry::SetSignature` или [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Сведения о типе также может возникать с помощью операции, в зависимости от представления внутренней функции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)