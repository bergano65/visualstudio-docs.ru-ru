---
title: IDebugProgramNodeAttach2::OnAttach | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 845ec66215c5d999aaf3b5c9658bc0fb8e7295a7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991132"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Присоединяется к соответствующую программу или откладывает процесс присоединения к [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] `GUID` Чтобы назначить соответствующую программу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) не следует вызывать метод. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается во время присоединения, прежде чем [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод. `OnAttach` Метод может выполнить сам процесс attach (в этом случае этот метод возвращает `S_FALSE`) или отложить процесс присоединения к `IDebugEngine2::Attach` метод ( `OnAttach` возвращает метод `S_OK`). В любом случае `OnAttach` можно задать метод `GUID` программы, отлаживаемой в данный `GUID`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
