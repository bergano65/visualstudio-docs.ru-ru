---
title: 'IDebugDisassemblyStream2:: DataSize | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6db80ef9c447f9e08a1332348d2212699d01d8e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203024"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает размер в инструкциях этого потока дизассемблированного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pnSize`  
 заполняет Возвращает размер в инструкциях.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Значение, возвращаемое этим методом, можно использовать для выделения массива структур [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md) , которые затем передаются в метод [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [дисассемблидата](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
