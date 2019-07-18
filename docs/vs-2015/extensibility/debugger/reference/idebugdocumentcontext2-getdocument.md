---
title: IDebugDocumentContext2::GetDocument | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fc4c522ace615b3c5d44244fc140d04cacf5387
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144972"
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает документ, который содержит контекст этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDocument`  
 [out] Возвращает [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , представляющий документ, который содержит контекст этого документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод предназначен для этих обработчиков отладки, которые поставляют документы непосредственно в интегрированной среде разработки. В противном случае этот метод должен возвращать `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
