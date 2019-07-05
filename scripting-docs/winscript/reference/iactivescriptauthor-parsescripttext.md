---
title: IActiveScriptAuthor::ParseScriptText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe6870f3b19c5727fdbea0418b8373b990cb671a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955098"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Выполняет синтаксический анализ текста скрипта, добавляет текст в скрипт создания ядра и создает `IScriptEntry` объект, соответствующий блок скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCode`  
 [in] Анализируемый текст скрипта.  
  
 `pszItemName`  
 [in] Адрес буфера, который содержит имя элемента, связанного с блоком скрипта.  
  
 `pszDelimiter`  
 [in] Адрес-объекта блок сценариев end разделитель. Когда `pszCode` анализируется из потока текста узел обычно использует разделитель (например, две одинарные кавычки), чтобы обнаружить завершение блока скрипта. Установите этот параметр значение NULL, если разделитель не для обозначения конца блока скрипта.  
  
 `dwCookie`  
 [in] Определяемое приложением значение, которая связана с новым `IScriptEntry` объекта.  
  
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