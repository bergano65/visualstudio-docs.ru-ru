---
title: IActiveScriptAuthor::GetEventHandler | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086688"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Возвращает сценария, с указанными атрибутами.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] `IDispatch` Объект, соответствующий `NamedItem` к которому присоединена сценария.  
  
 `pszItem`  
 [in] Адрес буфера идентификатор скриптлета полное доменное имя на узле верхнего уровня.  
  
 `pszSubItem`  
 [in] Адрес буфера идентификатор второго уровня скриптлета полное имя в узле. Значение NULL, если имя содержит только один уровень.  
  
 `pszEvent`  
 [in] Адрес буфера, который содержит имя события. Сценарий является обработчиком событий для данного события.  
  
 `ppse`  
 [out] Адрес переменной, которая получает указатель на `IScriptEntry` интерфейс сценария, с указанными атрибутами.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)