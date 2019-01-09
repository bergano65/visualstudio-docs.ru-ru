---
title: IActiveScriptAuthor::AddScriptlet | Документация Майкрософт
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
ms.openlocfilehash: 62499afe87a3d7dae31e609c9ce88f41e9d993a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089216"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Добавляет сценарий кода в качестве дочернего элемента корневого уровня `IScriptNode` объекта. В узле полное имя сценария разрешено иметь только два уровня.  
  
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
 [in] Адрес по умолчанию имя для связи со скриптлетом.  
  
 `pszCode`  
 [in] Адрес текста скриптлета.  
  
 `pszItemName`  
 [in] Адрес буфера идентификатор скриптлета полное доменное имя на узле верхнего уровня.  
  
 `pszSubItemName`  
 [in] Адрес буфера идентификатор второго уровня скриптлета полное имя в узле. Значение NULL, если имя содержит только один уровень.  
  
 `pszEventName`  
 [in] Адрес буфера, который содержит имя события, для которого сценария является обработчиком событий.  
  
 `pszDelimiter`  
 [in] Адрес-объекта блок сценариев end разделитель. Когда `pszCode` анализируется из потока текста узел обычно использует разделитель (например, две одинарные кавычки), чтобы обнаружить завершение блока скрипта. Установите этот параметр в значение NULL, если разделитель не отмечает конец блока скрипта.  
  
 `dwCookie`  
 [in] Определяемое приложением значение, используется для сопоставления сценария с объектом узла.  
  
 `dwFlags`  
 [in] Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)