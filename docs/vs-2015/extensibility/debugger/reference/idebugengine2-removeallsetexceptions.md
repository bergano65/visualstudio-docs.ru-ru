---
title: 'IDebugEngine2:: Ремовеаллсетексцептионс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 823c3312fe68d73ddd8db3d40a35cefbed1b9ac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196016"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Удаляет список исключений, установленных интегрированной средой разработки для определенной архитектуры или языка среды выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidType`  
 окне Идентификатор GUID для языка или GUID для модуля отладки, характерный для архитектуры времени выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Исключения, удаленные этим методом, были заданы предыдущими вызовами метода [сетексцептион](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .  
  
 Чтобы удалить конкретное исключение, вызовите метод [ремовесетексцептион](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
