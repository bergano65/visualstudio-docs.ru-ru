---
title: IDebugEngine3::SetJustMyCodeState | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 08d396d378f168b9a54e3b640e69dfeb3f6c9ba1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
 [in] Число структур сведения в`rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Массив [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) структур для использования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 JustMyCode является понятие отладки только код, к которой принадлежит пользователь и все промежуточного кода, такие как системный код игнорируется, даже если исходный код доступен для этого кода системы.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)