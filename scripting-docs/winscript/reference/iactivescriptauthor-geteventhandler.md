---
title: 'Иактивескриптаусор:: Жетевенсандлер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576228"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Возвращает скриптлет с указанными атрибутами.  
  
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
 окне Объект `IDispatch`, соответствующий `NamedItem`, к которому присоединена скриптлет.  
  
 `pszItem`  
 окне Буферный адрес идентификатора верхнего уровня полного имени скриптлет в узле.  
  
 `pszSubItem`  
 окне Адрес буфера второго уровня с полным именем скриптлет в узле. Задайте значение NULL, если имя имеет только один уровень.  
  
 `pszEvent`  
 окне Адрес буфера, содержащего имя события. Скриптлет — это обработчик событий для этого события.  
  
 `ppse`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `IScriptEntry` скриптлет с указанными атрибутами.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)