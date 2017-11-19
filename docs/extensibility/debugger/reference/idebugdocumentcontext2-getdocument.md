---
title: "IDebugDocumentContext2::GetDocument | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::GetDocument
helpviewer_keywords: IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 912f7f9499e7ce2f234c0d37fe0edeeb1935622c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
Получает документ, содержащий контекст этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [out] Возвращает [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) объект, представляющий документ, содержащий контекст этого документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод предназначен для этих отладчики, предлагающих документы непосредственно в Интегрированной среде разработки. В противном случае этот метод должен возвращать `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)