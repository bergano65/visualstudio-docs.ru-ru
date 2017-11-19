---
title: "IDebugStackFrame2::GetInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::GetInfo
helpviewer_keywords: IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b97acf264bfede855d96be90565e84b197e3e139
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Возвращает описание кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```csharp  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 [in] Сочетание флагов из [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисления, указывающее, какие поля `pFrameInfo` параметра должны быть заполнены.  
  
 `nRadix`  
 [in] Основание системы счисления, используемое в любой числовой сведения о форматировании.  
  
 `pFrameInfo`  
 [out] Объект [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуру, которая содержит описание кадра стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)