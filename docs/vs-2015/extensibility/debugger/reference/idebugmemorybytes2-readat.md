---
title: 'IDebugMemoryBytes2:: Реадат | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
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
 окне Объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , указывающий, с чего следует начать чтение байтов.  
  
 `dwCount`  
 окне Число байтов для чтения. Также указывает длину `rgbMemory` массива.  
  
 `rgbMemory`  
 [вход, выход] Массив заполняется фактически считанными байтами.  
  
 `pdwRead`  
 заполняет Возвращает число фактически считанных непрерывных байтов.  
  
 `pdwUnreadable`  
 [вход, выход] Возвращает число нечитаемых байтов. Может иметь значение null, если клиент неинтересен в количестве нечитаемых байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если запрашиваются 100 байт и первые 50 доступны для чтения, следующие 20 становятся нечитаемыми, а оставшиеся 30 читаются, этот метод возвращает:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 В этом случае, поскольку `*pdwRead + *pdwUnreadable < dwCount` вызывающий объект должен выполнить дополнительный вызов для чтения оставшихся 30 байт первоначально запрошенного 100, а объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , переданный в `pStartContext` параметре, должен иметь расширение 70.  
  
## <a name="see-also"></a>См. также:  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
