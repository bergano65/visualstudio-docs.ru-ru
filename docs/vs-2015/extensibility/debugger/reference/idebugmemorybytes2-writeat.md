---
title: 'IDebugMemoryBytes2:: Вритеат | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2479ac3948f81769ba2e73c746fd1811652aa239
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180566"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Записывает указанное число байтов памяти, начиная с указанного адреса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Объект [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , указывающий место начала записи байтов.  
  
 `dwCount`  
 [in] Количество записываемых байтов.  
  
 `rgbMemory`  
 окне Записываемые байты. Предполагается, что этот массив имеет размер не менее `dwCount` байт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение, `S_FALSE` если не все байты могут быть записаны или возвращали код ошибки (обычно `E_FAIL` ).  
  
## <a name="remarks"></a>Remarks  
 Если начальный адрес не находится в окне памяти, представленном этим объектом [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , то запись не происходит и возвращается код ошибки `E_FAIL` , даже если сумма для записи пересекается с областью памяти.  
  
## <a name="see-also"></a>См. также:  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
