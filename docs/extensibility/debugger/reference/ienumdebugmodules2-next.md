---
title: "IEnumDebugModules2::Next | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: bb4ebd3c5392114ba95e5cdbbfb71e8b5e7cdb5a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Возвращает следующий набор элементов из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число элементов для извлечения. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [in, out] Массив [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) элементы, которые должны заполняться в.  
  
 `pceltFetched`  
 [out] Возвращает количество элементов, фактически извлеченных в `rgelt`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше запрошенного числа элементов может быть возвращен; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
