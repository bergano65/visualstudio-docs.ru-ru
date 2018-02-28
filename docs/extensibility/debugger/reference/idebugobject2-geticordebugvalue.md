---
title: "IDebugObject2::GetICorDebugValue | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5b28e0cd6d66479479dbdb51825e0804abab06be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Возвращает объект управляемого кода, который представляет значение, связанное с этим объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUnk`  
 [out] `IUnknown` интерфейс, который представляет этот псевдоним. Этот интерфейс можно запрашивать `ICorDebugValue` интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `ICorDebugValue` Объект является интерфейсом среды CLR, который представляет значение.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)