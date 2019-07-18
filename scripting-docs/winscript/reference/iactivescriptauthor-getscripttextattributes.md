---
title: IActiveScriptAuthor::GetScriptTextAttributes | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75e0d5edf7cf2f83e814036cec56a1b19a89813e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955124"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Возвращает атрибуты текста для блока скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCode`  
 [in, size_is (`cch`)] текст блока скрипта. Эта строка не быть нулевым байтом.  
  
 `cch`  
 [in] Размер, используемый для `pszCode` и `pattr` параметров.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта. Когда `pszCode` анализируется из потока текста, узел обычно использует разделитель (например, две одинарные кавычки), чтобы определить конец скриптлета. Установите этот параметр значение NULL, если разделитель не для обозначения конца блока скрипта.  
  
 `dwFlags`  
 [in] Флаги, связанные с атрибутами текстового блока скрипта. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Определите идентификаторы, которые имеют атрибут SOURCETEXT_ATTR_IDENTIFIER и определить операторы точки, имеющие атрибут SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Определите текущего объекта, который имеет атрибут SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Определите строку содержимого и текст примечания, имеющего атрибут SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] сведения о цвете для код блока скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)