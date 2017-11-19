---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Позволяет промежуточных узлов определить способ обработки ошибок во время выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pErrorDebug`  
 [in] Возникшая ошибка во время выполнения  
  
 `pfEnterDebugger`  
 [out] Флаг, указывающий, следует ли передавать ошибки отладчику JIT-отладки.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Флаг, указывающий, следует ли вызывать `IActiveScriptSite::OnScriptError` Если пользователь решил продолжить без отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются значение в таблице ниже.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Промежуточный узел, этот метод можно использовать для определения способа обработки ошибок во время выполнения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)