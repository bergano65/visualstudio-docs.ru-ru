---
title: IDebugPortSupplier2::CanAddPort | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00b1c1303be8ccc326a58a20d132ad38db3b426d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113966"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Проверяет, что поставщика порта можно добавить новые порты.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если порт может быть добавлен, возвращает `S_OK`; в противном случае возвращает `S_FALSE` для указания порты не могут добавляться в этот поставщика порта.  
  
## <a name="remarks"></a>Примечания  
 Этот метод перед вызовом метода [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) метода, так как последний метод создает порт, а также добавление, который может быть длительной операции.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)