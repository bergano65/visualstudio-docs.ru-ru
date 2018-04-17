---
title: IDebugModule2::ReloadSymbols_Deprecated | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcd383130c1af1765014adfa438482543c336ede
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
УСТАРЕВШИЕ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ. Повторно загружает символы для данного модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszUrlToSymbols`  
 [in] Путь в хранилище символов.  
  
 `pbstrDebugMessage`  
 [out] Возвращает информационное сообщение, такие как состояние или сообщение об ошибке, который отображается справа от имени модуля в окне «модули».  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Модуль отладки всегда должны возвращать `E_FAIL`.  
  
## <a name="remarks"></a>Примечания  
 Этот метод больше не поддерживается. Реализуйте [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) метод вместо него.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)