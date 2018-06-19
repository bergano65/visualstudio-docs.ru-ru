---
title: IEnumDebugPorts2::Skip | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5369b4fa47eb31c7f40c0584b7b1c060ab41b119
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126690"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
Пропускает указанное число элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число пропускаемых элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если `celt` больше, чем количество оставшихся элементов; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если `celt` указывает значение, большее число оставшихся элементов перечисления имеет значение до конца и `S_FALSE` возвращается.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)