---
title: 'IScriptEntry:: Жетитемнаме | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575452"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Возвращает имя элемента, идентифицирующего объект `IScriptEntry`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 заполняет Адрес буфера, который содержит имя элемента. Имя элемента используется узлом для обнаружения записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Для `IScriptScriptlet`ных объектов имя элемента задается с помощью [иактивескриптаусор:: аддскриптлет](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Для других интерфейсов имя элемента задается с помощью [IScriptEntry:: сетитемнаме](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)