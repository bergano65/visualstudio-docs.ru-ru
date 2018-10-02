---
title: IDebugFunctionObject::CreateArrayObject | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f996e7b58150f1340bf7a47790696a54f4cbc7fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559682"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugFunctionObject::CreateArrayObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfunctionobject-createarrayobject).  
  
Создает объект массива. Этот массив может содержать либо примитив или объект значения экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

