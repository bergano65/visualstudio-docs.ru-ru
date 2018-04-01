---
title: IDebugCodeContext2::GetLanguageInfo | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6bb29ddf1ebbaafffc316562604d3e7b6cba8ff5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Возвращает сведения о языке для этого контекста кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrLanguage`  
 [in, out] Возвращает строку, содержащую имя языка, например «C++».  
  
 `pguidLanguage`  
 [in, out] Возвращает идентификатор GUID для языка кода контекста, например, `guidCPPLang`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 По крайней мере один из параметров должен возвращать значение отличное от null.  
  
## <a name="see-also"></a>См. также  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)