---
title: 'IScriptEntry:: Сетитемнаме | Документация Майкрософт'
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
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575370"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Задает имя элемента, идентифицирующего объект `IScriptEntry`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 окне Адрес буфера, который содержит имя элемента. Имя элемента используется узлом для обнаружения записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Метод не был успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Для `IScriptEntry` объектов этот метод возвращает `S_OK`.  
  
 Для `IScriptScriptlet` объектов (которые являются производными от `IScriptEntry`) Этот метод возвращает `E_FAIL`. Для `IScriptScriptlet` объектов имя элемента задается [иактивескриптаусор:: аддскриптлет](../../winscript/reference/iactivescriptauthor-addscriptlet.md) и не может быть изменено.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)