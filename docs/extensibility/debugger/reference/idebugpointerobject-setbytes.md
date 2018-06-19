---
title: IDebugPointerObject::SetBytes | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8234117d7965c4f2e471855d39ed0c3cee1f88c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114298"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Задает значение, на который указывает из серии последовательных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwStart`  
 [in] Указывает смещение в байтах от начала объекта.  
  
 `dwCount`  
 [in] Число байтов для задания.  
  
 `pBytes`  
 [in] Массив байтов, представляющий новое значение. Это значение хранится в объект, начиная с заданного смещения.  
  
 `pdwBytes`  
 [out] Возвращает число байтов, фактически набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется в том случае, если указатель, представленного этим экземпляром [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на тип-примитив или простого массива типов-примитивов (то есть, массив, может быть представлена простая последовательность байтов). Это `IDebugPointerObject` объект не может быть пустая ссылка (оно должно указывать на адрес в памяти).  
  
## <a name="see-also"></a>См. также  
 [Метод GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)