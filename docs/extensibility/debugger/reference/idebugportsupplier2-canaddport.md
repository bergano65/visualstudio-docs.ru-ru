---
title: IDebugPortSupplier2::CanAddPort | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 18d728f762a9e4dd16930e4634c9cb0ca47b2bc8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853909"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Проверяет, что поставщик порта можно добавить новые порты.  
  
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
 Можно ли добавить порт, возвращает `S_OK`; в противном случае возвращает `S_FALSE` для указания порты не могут добавляться к этого поставщика порта.  
  
## <a name="remarks"></a>Примечания  
 Вызовите этот метод перед вызовом [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) метод, так как последний метод создает порт, а также добавление, которая может оказаться длительной операции.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)