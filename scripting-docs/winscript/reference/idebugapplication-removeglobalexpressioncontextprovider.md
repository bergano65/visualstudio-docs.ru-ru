---
title: 'IDebugApplication:: Ремовеглобалекспрессионконтекстпровидер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveGlobalExpressionContextProvider
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b948cea02d696b6c176e925adf9c95913be2cd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571136"
---
# <a name="idebugapplicationremoveglobalexpressioncontextprovider"></a>IDebugApplication::RemoveGlobalExpressionContextProvider
Удаляет из этого приложения поставщик контекста глобального выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCookie`  
 окне Файл cookie, возвращенный методом `AddGlobalExpressionContextProvider` при добавлении поставщика глобального контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Метод `RemoveGlobalExpressionContextProvider` удаляет из этого приложения поставщик контекста глобального выражения.  
  
## <a name="see-also"></a>См. также  
 [IDebugApplication:: аддглобалекспрессионконтекстпровидер](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)    
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)