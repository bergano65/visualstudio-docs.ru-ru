---
title: IEnumDebugPropertyInfo2::Skip | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2::Skip
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Skip
ms.assetid: 0366c778-18eb-4065-a452-64b70c751a58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca619af21949d5988f598646475fad4ff04c632d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124723"
---
# <a name="ienumdebugpropertyinfo2skip"></a>IEnumDebugPropertyInfo2::Skip
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
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)