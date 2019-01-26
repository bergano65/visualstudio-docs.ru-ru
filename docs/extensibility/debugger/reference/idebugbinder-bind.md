---
title: IDebugBinder::Bind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82455db074e23b5ea08010747c80888e4629cf18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979963"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Этот метод получает контекст в памяти или объект, содержащий текущее значение символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pContainer`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , содержащая дочерние ссылается `pField`.  
  
 `pField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , представляющий символ.  
  
 `ppObject`  
 [out] Возвращает `IDebugObject` , представляющий экземпляр символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)