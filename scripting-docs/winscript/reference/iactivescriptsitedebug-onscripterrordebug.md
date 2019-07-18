---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50e8c7baa42d6f2f36dc71b768797dfe2a464bf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992431"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Позволяет промежуточный узел определить способ обработки ошибок времени выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pErrorDebug`  
 [in] Возникшей ошибки времени выполнения  
  
 `pfEnterDebugger`  
 [out] Флаг, указывающий, следует ли передать ошибку в отладчик для JIT-отладки.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Флаг, указывающий, следует ли вызывать `IActiveScriptSite::OnScriptError` когда пользователь решает продолжить без отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Возможные значения включают, но не ограничиваются значение в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Промежуточный узел, этот метод можно использовать для определения способа обработки ошибок времени выполнения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)