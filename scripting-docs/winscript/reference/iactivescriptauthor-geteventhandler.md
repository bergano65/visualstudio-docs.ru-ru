---
title: "IActiveScriptAuthor::GetEventHandler | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Возвращает сценарий, который с указанными атрибутами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdisp`  
 [in] `IDispatch` Объект, соответствующий `NamedItem` к которой подключен сценариев.  
  
 `pszItem`  
 [in] Адрес буфера верхнего уровня идентификатор сценариев полное имя в узле.  
  
 `pszSubItem`  
 [in] Адрес буфера идентификатор второго уровня с именем полный сценарий в узле. Значение NULL, если имя содержит только один уровень.  
  
 `pszEvent`  
 [in] Адрес буфера, который содержит имя события. Сценарий является обработчиком событий для данного события.  
  
 `ppse`  
 [out] Адрес переменной, которая получает указатель на `IScriptEntry` интерфейс сценариев, с указанными атрибутами.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)