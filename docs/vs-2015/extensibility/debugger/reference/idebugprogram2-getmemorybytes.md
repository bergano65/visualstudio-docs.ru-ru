---
title: 'IDebugProgram2:: Жетмеморибитес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f4c160799a48e7c548425ed18809bbf9cb381ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148687"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает байты памяти, занятые программой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppMemoryBytes`  
 заполняет Возвращает объект [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , представляющий байты памяти программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Байт памяти, представленный объектом [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , предназначен для образа программы в памяти, а не для памяти, которая была выделена при выполнении программы.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
