---
title: IDebugModule3::LoadSymbols | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14406d0aeb58cead006ef9f1d5485a053d4a72c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021066"
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
 Если метод завершается успешно, возвращается `S_OK`. Если происходит сбой, он возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод загружает символы из текущего пути поиска (который может быть изменен путем вызова [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) метод).  
  
 Этот метод является предпочтительным, чем [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)