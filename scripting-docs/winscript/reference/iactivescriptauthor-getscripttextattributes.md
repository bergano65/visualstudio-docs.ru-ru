---
title: IActiveScriptAuthor::GetScriptTextAttributes | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645524"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Возвращает атрибуты текста для блока сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in, size_is (`cch`)] текстового блока скрипта. Эта строка не быть нулем.  
  
 `cch`  
 [in] Размер, используемый для `pszCode` и `pattr` параметров.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта. Когда `pszCode` анализируется из текстового потока, узел обычно использует разделитель (например, две одинарных кавычки), чтобы обнаружить завершение сценариев. Установите этот параметр значение NULL, если разделитель не для идентификации конца блока скрипта.  
  
 `dwFlags`  
 [in] Флаги, связанные с атрибутами текстового блока скрипта. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Определить идентификаторы, имеющие атрибут SOURCETEXT_ATTR_IDENTIFIER и идентификации точки операторов, имеющих атрибут SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Определите текущего объекта, имеющего атрибут SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Определите строку содержимого и текст комментария, имеющего атрибут SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out size_is (`cch`)] цвет шрифта для код блока скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)