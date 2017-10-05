---
title: "IDebugProgramNodeAttach2::OnAttach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e0162d17fc81b1304213d0259863f35523a833f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Присоединяет к соответствующую программу или откладывает процесс присоединения к [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidProgramId`  
 [in] `GUID` присвоить соответствующую программу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод не должен вызываться. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается во время процесса подключения перед [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод. `OnAttach` Метод может выполнить сам процесс присоединения (в этом случае этот метод возвращает `S_FALSE`) или отложить процесс присоединения к `IDebugEngine2::Attach` метод ( `OnAttach` возвращает метод `S_OK`). В любом случае `OnAttach` можно задать метод `GUID` для отлаживаемой программы данного `GUID`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
