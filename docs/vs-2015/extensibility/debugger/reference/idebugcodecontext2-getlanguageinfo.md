---
title: IDebugCodeContext2::GetLanguageInfo | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0df2a08dd7906b9c4c0935d90150037a3bc0275a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990690"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает сведения о языке для этого контекста кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 По крайней мере один из параметров должен возвращать значение отличное от null.  
  
## <a name="see-also"></a>См. также  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
