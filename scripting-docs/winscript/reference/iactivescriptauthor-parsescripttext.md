---
title: Иактивескриптаусор::P Арсескрипттекст | Документация Майкрософт
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
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576150"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Анализирует текст скрипта, добавляет текст в подсистему создания скриптов и создает объект `IScriptEntry`, соответствующий блоку скрипта.  
  
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
 окне Анализируемый текст скрипта.  
  
 `pszItemName`  
 окне Адрес буфера, содержащий имя элемента, связанного с блоком скрипта.  
  
 `pszDelimiter`  
 окне Адрес разделителя-блока конца скрипта. Когда `pszCode` анализируется из потока текста, узел обычно использует разделитель (например, две одинарные кавычки) для обнаружения конца блока скрипта. Присвойте этому параметру значение NULL, если нет разделителя для обнаружения конца блока скрипта.  
  
 `dwCookie`  
 окне Определяемое приложением значение, связанное с новым объектом `IScriptEntry`.  
  
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