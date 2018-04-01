---
title: IDebugExceptionEvent2::CanPassToDebuggee | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3a443b3f88ec64d24ea7a5bf4db682e5aa10b2eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Определяет, поддерживает ли модуль отладки (DE) передать это исключение для отлаживаемой при возобновлении выполнения программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает один `S_OK` (исключение может быть передан программой) или `S_FALSE` (исключение не может быть передано в).  
  
## <a name="remarks"></a>Примечания  
 DE должен иметь действия по умолчанию для передачи отлаживаемому процессу. Может появиться в Интегрированной среде разработки [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событий и вызовов [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md) метод без вызова `CanPassToDebuggee` метод. Таким образом DE должен регистра по умолчанию для передачи исключение, или нет.  
  
## <a name="see-also"></a>См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)