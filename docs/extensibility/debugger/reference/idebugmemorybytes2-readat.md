---
title: "IDebugMemoryBytes2::ReadAt | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f4c71da3152394442d63c937b77e4f6538fcc1ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Считывает последовательность байтов, начиная с заданной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [in] Число байтов для чтения. Также указывает длину `rgbMemory` массива.  
  
 `rgbMemory`  
 [in, out] Фактически считанных заполнено байты массива.  
  
 `pdwRead`  
 [out] Возвращает число фактически считанных смежных байтов.  
  
 `pdwUnreadable`  
 [in, out] Возвращает число байтов, может быть прочитан. Может иметь значение null, если клиент не хочет число байтов может быть прочитан.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если запрашиваются 100 байт и первый 50 доступны для чтения, далее 20 не читаются, а оставшиеся 30 доступны для чтения, этот метод возвращает:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 В этом случае из-за `*pdwRead + *pdwUnreadable < dwCount`, вызывающий объект необходимо внести дополнительный вызов для чтения оставшиеся 30 байт из исходного запрошенный 100 и [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) переданный объект `pStartContext` параметра необходимо дополнительно на 70.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)