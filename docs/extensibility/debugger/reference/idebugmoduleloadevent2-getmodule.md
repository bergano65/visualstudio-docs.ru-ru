---
title: "IDebugModuleLoadEvent2::GetModule | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModuleLoadEvent2::GetModule
helpviewer_keywords: IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4bd5ebf74bb3818aff06e01b7c6d181760510f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Возвращает модуль, для которого создается загружен или выгружен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pModule`  
 [out] Возвращает [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий модуль, который загрузкой или выгрузкой.  
  
 `pbstrDebugMessage`  
 [in, out] Возвращает необязательное сообщение, описывающее данное событие. Если этот параметр имеет значение null, сообщение не было запрошено.  
  
 `pbLoad`  
 [in, out] Ненулевое значение (`TRUE`) Если модуль является загрузка и ноль (`FALSE`) Если выгрузки модуля. Если этот параметр имеет значение null, состояние не было запрошено.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)