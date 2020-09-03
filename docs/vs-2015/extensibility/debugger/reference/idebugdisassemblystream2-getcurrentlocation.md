---
title: 'IDebugDisassemblyStream2:: Жеткуррентлокатион | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 133a46c273fed04ad95bb52076b1d5d172cc0517
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196213"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает идентификатор расположения кода, представляющий текущее расположение кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCurrentLocation(   
   UINT64* puCodeLocationId  
);  
```  
  
```csharp  
int GetCurrentLocation(   
   out ulong puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `puCodeLocationId`  
 заполняет Возвращает идентификатор расположения кода. Описание идентификатора расположения кода см. в разделе "Примечания" для метода [жеткоделокатионид](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор расположения кода можно преобразовать в контекст кода, вызвав метод [жеткодеконтекст](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [жеткоделокатионид](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
