---
title: IDebugMemoryBytes2::WriteAt | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d1d79d88baf9688fe68ff44d59dcd4d19baf9f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112126"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Записывает указанное число байтов памяти, начиная с указанного адреса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStartContext`  
 [in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) объект, который указывает, где начинается запись байтов.  
  
 `dwCount`  
 [in] Число байтов для записи.  
  
 `rgbMemory`  
 [in] Запись байтов. Этот массив полагается равным по крайней мере `dwCount` размер байт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если не все байты, может быть записан или возвращает код ошибки (обычно `E_FAIL`).  
  
## <a name="remarks"></a>Примечания  
 Если начальный адрес не находится в окне памяти, представленный этим [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) объекта, запись не выполняется и код ошибки `E_FAIL` возвращается, даже если сумма для записи перекрывает области памяти.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)