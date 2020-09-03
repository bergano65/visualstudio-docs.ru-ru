---
title: 'Идебугпоинтеробжект:: SetBytes | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d467b037f4e2affea53a142304507f876630999
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202959"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает значение, на которое указывает последовательность последовательных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Смещение в байтах от начала объекта, на который указывает.  
  
 `dwCount`  
 окне Число байтов, которое необходимо задать.  
  
 `pBytes`  
 окне Массив байтов, представляющий новое значение. Это значение сохраняется в объект, начиная с заданного смещения.  
  
 `pdwBytes`  
 заполняет Возвращает число фактически установленных байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод используется, если указатель, представленный этим [идебугпоинтеробжект](../../../extensibility/debugger/reference/idebugpointerobject.md) , указывает на примитивный тип или простой массив типов-примитивов (то есть массив, который может быть представлен простой последовательностью байтов). Этот `IDebugPointerObject` объект не может быть пустой ссылкой (он должен указывать на адрес в памяти).  
  
## <a name="see-also"></a>См. также:  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
