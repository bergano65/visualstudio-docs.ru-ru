---
title: IDebugModule3::LoadSymbols | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1b3dda16ac3312e7deec21b06a4df05162bfa692
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Загрузка символов для текущего модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод выполнен успешно, возвращается значение `S_OK`. Если не удается, возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод загружает символы из текущего пути поиска (который может быть изменен путем вызова [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) метода).  
  
 Этот метод является предпочтительным, чем [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)