---
title: IDebugPortSupplier2::CanAddPort | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6b493229ab33f628c54580711604b16a4e2b5c5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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