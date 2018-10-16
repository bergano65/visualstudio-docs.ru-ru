---
title: IActiveScriptAuthor::AddScriptlet | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645664"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Добавляет код пользователи в качестве дочернего элемента корневого уровня `IScriptNode` объекта. В узле полное имя сценариев допускается иметь только двух уровней.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Адрес по умолчанию имя, связанное с помощью сценариев.  
  
 `pszCode`  
 [in] Адрес текст сценариев.  
  
 `pszItemName`  
 [in] Адрес буфера верхнего уровня идентификатор сценариев полное имя в узле.  
  
 `pszSubItemName`  
 [in] Адрес буфера идентификатор второго уровня с именем полный сценарий в узле. Значение NULL, если имя содержит только один уровень.  
  
 `pszEventName`  
 [in] Адрес буфера, который содержит имя события, для которого сценариев является обработчиком событий.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта блока. Когда `pszCode` анализируется из текстового потока, узел обычно использует разделитель (например, две одинарных кавычки), для определения конца блока скрипта. Установите этот параметр в значение NULL, если разделитель не отмечает конец блока скрипта.  
  
 `dwCookie`  
 [in] Определяемые приложением значения, используемый для связи с объектом узла сценариев.  
  
 `dwFlags`  
 [in] Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)