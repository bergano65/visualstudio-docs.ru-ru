---
title: IDebugFunctionObject::CreateArrayObject | Документация Майкрософт
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
ms.openlocfilehash: 150380d77b6e59cf6db822bca7f674759fb8a56f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873781"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Создает объект массива. Этот массив может содержать либо примитив или объект значения экземпляра.  
  
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
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, представляющий класс объекта, который, если создается массив объектов значениями экземпляра. Если создается массив простых объектов, этот параметр является значение null.  
  
 `dwRank`  
 [in] Ранг или число измерений массива.  
  
 `dwDims`  
 [in] Размер каждого измерения массива.  
  
 `dwLowBounds`  
 [in] Источник каждого измерения (обычно 0 или 1).  
  
 `ppObject`  
 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект, представляющий только что созданный массив. На самом деле [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызовите этот метод, чтобы создать объект, представляющий параметру массива в функцию, который представляется [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)