---
title: IDebugDocumentPosition2::IsPositionInDocument | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 225a92d521f118c2d038cabf114c69f389af0108
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Определяет, содержится ли в документе данной позиции документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDoc`  
 [in] [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , представляющий потенциальных содержащего документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется главным образом задание точек останова [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейсов. После загрузки документов положение точки останова вызывается для определения, содержит ли документ этой позиции.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)