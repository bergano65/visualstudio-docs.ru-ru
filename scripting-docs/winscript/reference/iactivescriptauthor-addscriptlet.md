---
title: 'Иактивескриптаусор:: Аддскриптлет | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577976"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Добавляет код скриптлет в качестве дочернего объекта `IScriptNode` корневого уровня. В узле полное имя скриптлет может иметь только два уровня.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszDefaultName`  
 окне Адрес имени по умолчанию, связываемого с скриптлет.  
  
 `pszCode`  
 окне Адрес скриптлет текста.  
  
 `pszItemName`  
 окне Буферный адрес идентификатора верхнего уровня полного имени скриптлет в узле.  
  
 `pszSubItemName`  
 окне Адрес буфера второго уровня с полным именем скриптлет в узле. Задайте значение NULL, если имя имеет только один уровень.  
  
 `pszEventName`  
 окне Адрес буфера, содержащего имя события, для которого скриптлет является обработчиком событий.  
  
 `pszDelimiter`  
 окне Адрес разделителя-блока конца скрипта. Когда `pszCode` анализируется из потока текста, узел обычно использует разделитель (например, две одинарные кавычки) для обнаружения конца блока скрипта. Присвойте этому параметру значение NULL, если разделитель не отмечает конец блока скрипта.  
  
 `dwCookie`  
 окне Определяемое приложением значение, которое используется для связывания скриптлет с объектом узла.  
  
 `dwFlags`  
 окне Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)