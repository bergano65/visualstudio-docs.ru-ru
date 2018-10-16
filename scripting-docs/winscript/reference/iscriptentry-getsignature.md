---
title: IScriptEntry::GetSignature | Документы Microsoft
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
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729324"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Возвращает сведения о типе для `IScriptEntry` объект функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppti`  
 [out] Введите сведения, связанные с этим `IScriptEntry` объект функции.  
  
 `piMethod`  
 [out] Метод индекса в `ITypeInfo` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Сведения о типе устанавливается с помощью [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) или [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Сведения о типе также можно создать с помощью операции, в зависимости от представления внутренней функции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)