---
title: 'IDebugExpressionEvaluator2:: Сетидебугидекаллбакк | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de8f67f8ba501a9c97ad1fd1d0de58711ae0c52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149025"
---
# <a name="idebugexpressionevaluator2setidebugidecallback"></a>IDebugExpressionEvaluator2::SetIDebugIDECallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Позволяет модулю отладки передавать обратный вызов средству оценки выражений во время инициализации.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetIDebugIDECallback (  
   IDebugIDECallback * pCallback  
);  
```  
  
```csharp  
int SetIDebugIDECallback (  
   IDebugIDECallback pCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCallback`  
 окне Интерфейс для обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
