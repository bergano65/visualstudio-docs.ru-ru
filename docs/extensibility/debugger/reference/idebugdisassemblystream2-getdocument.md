---
title: IDebugDisassemblyStream2::GetDocument | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetDocument
helpviewer_keywords:
- IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7483ab7fdcc66cef0becbc9e4e42e35c310fdd14
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
Возвращает исходный документ, связанный с этого входного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDocument(   
   BSTR              bstrDocumentUrl,  
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   string              bstrDocumentUrl,  
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrDocumentUrl`  
 [in] URL-адрес документа.  
  
 `ppDocument`  
 [out] Возвращает [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) объект, представляющий документ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод реализуется отладчики, которые имеют текстовые документы, которые не хранятся в файле фактические.  
  
## <a name="see-also"></a>См. также  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)