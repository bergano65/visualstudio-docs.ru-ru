---
title: IDebugEngine3::SetJustMyCodeState | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fda672cc9d6861520b9da3a894b94d51f4100683
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121629"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Этот метод указывает модуль отладки о JustMyCode сведения о состоянии.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fUpdate`  
 [in] Ненулевое значение (`TRUE`) чтобы обновить текущие данные, ноль (`FALSE`) для сброса всех сведения (без учета все ранее значения).  
  
 `dwModules`  
 [in] Число структур сведения в `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Массив [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) структур для использования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 JustMyCode является понятие отладки только код, к которой принадлежит пользователь и все промежуточного кода, такие как системный код игнорируется, даже если исходный код доступен для этого кода системы.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)