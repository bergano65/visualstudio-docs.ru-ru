---
title: IDebugFunctionObject::CreateArrayObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39695d37012f90d7e61c04f64ee1c05f11482373
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Создает объект массива. Этот массив может содержать либо примитив или экземпляр значений объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ot`  
 [in] Указывает значение из [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) перечисление, указывающее тип объекта нового массива.  
  
 `pClassField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, представляющий класс объекта, если создается массив объектов значения экземпляра. Если создается массив простых объектов, этот параметр является значение null.  
  
 `dwRank`  
 [in] Число измерений массива или рангом.  
  
 `dwDims`  
 [in] Размер каждого измерения массива.  
  
 `dwLowBounds`  
 [in] Источник для каждого измерения (обычно 0 или 1).  
  
 `ppObject`  
 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект, представляющий вновь созданный массив. Это на самом деле [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызовите этот метод, чтобы создать объект, представляющий параметр массива в функцию, который представляется [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)