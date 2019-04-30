---
title: IScriptEntry::SetItemName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25ac4977f1fca44d63767c372db169f8cb61ea6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787662"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Задает имя элемента, который идентифицирует `IScriptEntry` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 [in] Адрес буфера, который содержит имя элемента. Имя элемента используется приложением для идентификации записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Метод завершилась неудачно.|  
  
## <a name="remarks"></a>Примечания  
 Для `IScriptEntry` объектов, этот метод возвращает `S_OK`.  
  
 Для `IScriptScriptlet` объектов (который являются производными от `IScriptEntry`), этот метод возвращает `E_FAIL`. Для `IScriptScriptlet` объектов задается имя элемента [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) и не может быть изменено.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)