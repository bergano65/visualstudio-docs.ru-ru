---
title: IDebugMemoryBytes2::ReadAt | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180577"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Считывает последовательность байтов, начиная с заданного расположения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStartContext`  
 [in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, который указывает, где начинается чтение байтов.  
  
 `dwCount`  
 [in] Число байтов для чтения. Также определяет длину `rgbMemory` массива.  
  
 `rgbMemory`  
 [in, out] Массив, заполненный байты непосредственного чтения.  
  
 `pdwRead`  
 [out] Возвращает число фактически считанных смежных байтов.  
  
 `pdwUnreadable`  
 [in, out] Возвращает число байтов, может быть прочитан. Может иметь значение null, если клиент не хочет число байтов, может быть прочитан.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если запросу 100 байт и первые 50 доступны для чтения, не читаются еще 20, а оставшиеся 30 доступны для чтения, этот метод возвращает:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 В этом случае так как `*pdwRead + *pdwUnreadable < dwCount`, вызывающий объект должен делать дополнительный вызов для чтения оставшихся 30 байт из исходного запроса 100 и [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) переданный объект `pStartContext` параметр должен быть advanced на 70.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
