---
title: IDebugCanStopEvent2::GetDocumentContext | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e5b9bbd5127ac3cf7aef70744fc80ebc8372dfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Возвращает контекст документ, описывающий расположение этого события.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDocCxt`  
 [out] Возвращает [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс, который представляет позицию в соответствующий файл исходного документа для текущего расположения в коде.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило контекст документа может рассматриваться как положение в файле исходного кода.  
  
 Чтобы получить контекст кода, который ориентировано на достижение код инструкции, вызовите [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)