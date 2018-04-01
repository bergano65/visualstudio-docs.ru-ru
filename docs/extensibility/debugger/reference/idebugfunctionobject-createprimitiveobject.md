---
title: IDebugFunctionObject::CreatePrimitiveObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c72dd6d804c37496d2615ccd086ee095c75510d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Создает объект примитив, например простой целое число со знаком.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ot`  
 [in] Значение из [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) перечисление, представляющее тип примитива, для создания.  
  
 `ppObject`  
 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) представляет вновь созданный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается для создания объекта, который представляет объект-примитив, — это параметр для функции, которая представлена [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейса. Например если строка выражения «myString(5)», этот метод будет использоваться для создания объекта, представляющего целочисленное значение 5.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)