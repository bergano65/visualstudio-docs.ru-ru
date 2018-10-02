---
title: IDebugModuleLoadEvent2::GetModule | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dcf01689b6ab133ee52870ff65293ab31e98855e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557515"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugModuleLoadEvent2::GetModule](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmoduleloadevent2-getmodule).  
  
Возвращает модуль, для которого создается загрузке или выгрузке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in, out] Возвращает необязательное сообщение, описывающее данное событие. Если этот параметр имеет значение null, сообщение не запрашивается.  
  
 `pbLoad`  
 [in, out] Ненулевое значение (`TRUE`) Если модуль является загрузка и ноль (`FALSE`) Если модуль выгружается. Если этот параметр имеет значение null, состояние не запрашивается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)

