---
title: IDebugModule2::ReloadSymbols_Deprecated | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 182561200e6239520b1345f43cc0a150baa30622
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961313"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. Повторно загружает символы для этого модуля.  
  
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
 [out] Возвращает информационное сообщение, такие как состояние или сообщения об ошибке, которое отображается в правой части имя модуля в окно "Модули".  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Модуль отладки всегда должны возвращать `E_FAIL`.  
  
## <a name="remarks"></a>Примечания  
 Этот метод больше не поддерживается. Реализуйте [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) метод вместо этого.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)