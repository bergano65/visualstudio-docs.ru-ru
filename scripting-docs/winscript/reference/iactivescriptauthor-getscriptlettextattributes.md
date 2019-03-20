---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155856"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Возвращает атрибуты текста скриптлета.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCode`  
 [in, size_is (`cch`)] текста скриптлета. Эта строка не быть нулевым байтом.  
  
 `cch`  
 [in] Размер, используемый для `pszCode` и `pattr` параметров.  
  
 `pszDelimiter`  
 [in] Адрес end-разделителя конца скриптлета. Когда `pszCode` анализируется из потока текста, узел обычно использует разделитель (например, две одинарные кавычки), чтобы определить конец скриптлета. Установите этот параметр в значение NULL, если разделитель не используется для идентификации конца сценария.  
  
 `dwFlags`  
 [in] Флаги, связанные с атрибутами текст сценария. Может быть сочетанием следующих значений.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Определите идентификаторы, которые имеют атрибут SOURCETEXT_ATTR_IDENTIFIER и определить операторы точки, имеющие атрибут SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Определите текущего объекта, который имеет атрибут SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Определите строку содержимого и текст примечания, имеющего атрибут SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] сведения о цвете для кода скриптлета.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)