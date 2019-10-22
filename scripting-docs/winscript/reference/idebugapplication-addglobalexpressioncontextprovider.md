---
title: 'IDebugApplication:: Аддглобалекспрессионконтекстпровидер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddGlobalExpressionContextProvider
ms.assetid: 35db7124-6970-4e45-8f00-ecdf21e9f5cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 429e87def1e17a6abac92ce2d3538960659cfaeb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573464"
---
# <a name="idebugapplicationaddglobalexpressioncontextprovider"></a>IDebugApplication::AddGlobalExpressionContextProvider
Добавляет поставщик контекста глобального выражения в это приложение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddGlobalExpressionContextProvider(  
   IProvideExpressionContexts*  pdsfs,  
   DWORD_PTR*                   pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdsfs`  
 окне Поставщик глобального контекста для добавления в это приложение.  
  
 `pdwCookie`  
 заполняет Файл cookie, который используется для удаления этого поставщика контекста глобального выражения из приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод добавляет в это приложение поставщик контекста глобального выражения.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)