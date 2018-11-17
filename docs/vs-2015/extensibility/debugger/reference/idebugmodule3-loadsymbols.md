---
title: IDebugModule3::LoadSymbols | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db6a6464bb60949f9cdd3bdf38c459319420213a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724233"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Загрузка символов для текущего модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

