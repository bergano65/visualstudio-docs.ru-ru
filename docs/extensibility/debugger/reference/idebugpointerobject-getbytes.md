---
title: "IDebugPointerObject::GetBytes | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::GetBytes
helpviewer_keywords: IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5e07ab129cb49ffba892ba3b681e6239d4477256
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Возвращает значение, указанное как ряд последовательных байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwStart`  
 [in] Указывает смещение в байтах от начала объекта.  
  
 `dwCount`  
 [in] Число извлекаемых байтов.  
  
 `pBytes`  
 [in, out] Массив, который будет заполнено значением, как ряд последовательных байтах, начиная с заданного смещения из объекта указывает.  
  
 `pdwBytes`  
 [out] Возвращает число байтов, фактически полученных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется в том случае, если указатель, представленного этим экземпляром [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на тип-примитив или простого массива типов-примитивов (то есть, массив, может быть представлена простая последовательность байтов).  
  
## <a name="see-also"></a>См. также  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)