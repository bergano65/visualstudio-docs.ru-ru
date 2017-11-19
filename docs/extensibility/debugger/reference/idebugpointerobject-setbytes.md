---
title: "IDebugPointerObject::SetBytes | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::SetBytes
helpviewer_keywords: IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91e11f0e321e286eaf669b50d2fa564fa29df314
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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