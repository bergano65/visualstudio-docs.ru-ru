---
title: 'IDebugDocumentContext2:: \ Document | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144972"
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает документ, содержащий этот контекст документа.  
  
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
 заполняет Возвращает объект [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , представляющий документ, содержащий этот контекст документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод предназначен для модулей отладки, предоставляя документы непосредственно в интегрированной среде разработки. В противном случае этот метод должен возвращать значение `E_NOTIMPL` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
