---
title: "IActiveScriptAuthor::ParseScriptText | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Выполняет синтаксический анализ текста сценария, добавляет текст в скрипт создания ядра и создает `IScriptEntry` объект, соответствующий блок сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Анализируемый текст сценария.  
  
 `pszItemName`  
 [in] Адрес буфера, который содержит имя элемента, связанного с блоком сценария.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта блока. Когда `pszCode` анализируется из текстового потока, узел обычно использует разделитель (например, две одинарных кавычки), для определения конца блока скрипта. Установите этот параметр значение NULL, если разделитель не для идентификации конца блока скрипта.  
  
 `dwCookie`  
 [in] Определяемые приложением значения, связанного с новым `IScriptEntry` объекта.  
  
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