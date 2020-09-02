---
title: 'IDebugModule3:: Лоадсимболс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46385a61c5cc8cc30f75fd06a55bbe155e045f0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157287"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Загружает символы для текущего модуля.  
  
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
 Если метод завершается успешно, возвращает значение `S_OK`. В противном случае функция возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод загружает символы из текущего пути поиска (который можно изменить, вызвав метод [сетсимболпас](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) ).  
  
 Этот метод является предпочтительным по сравнению с методом [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
