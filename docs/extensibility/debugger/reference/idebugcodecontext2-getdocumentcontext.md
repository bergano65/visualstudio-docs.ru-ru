---
title: "IDebugCodeContext2::GetDocumentContext | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetDocumentContext
helpviewer_keywords: IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 335b8f7a2c92b299d62cda0f23c7d727cad653b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Возвращает контекст документа, соответствующий контексту этого кода. Контекст документа представляет позицию в исходный файл, соответствующий исходный код, созданный в этой инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppSrcCxt`  
 [out] Возвращает [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объект, соответствующий контекст кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило контекст документа может рассматриваться как положение в файле исходного кода при положения в потоке выполнения инструкции кода контекст кода.  
  
## <a name="see-also"></a>См. также  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)