---
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ce816e20e59d407f9b3cd84e3dffa703d84a324
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189545"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. Перезагружает символы для этого модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Путь к хранилищу символов.  
  
 `pbstrDebugMessage`  
 заполняет Возвращает информационное сообщение, например состояние или сообщение об ошибке, которое отображается справа от имени модуля в окне модули.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Модуль отладки должен всегда возвращать значение `E_FAIL` .  
  
## <a name="remarks"></a>Remarks  
 Этот метод больше не поддерживается. Вместо этого реализуйте метод [лоадсимболс](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
