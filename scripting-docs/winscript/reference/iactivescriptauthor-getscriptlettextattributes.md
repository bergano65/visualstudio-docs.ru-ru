---
title: "IActiveScriptAuthor::GetScriptletTextAttributes | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Возвращает атрибуты текста пользователи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in, size_is (`cch`)] текст сценариев. Эта строка не быть нулем.  
  
 `cch`  
 [in] Размер, используемый для `pszCode` и `pattr` параметров.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из сценариев. Когда `pszCode` анализируется из текстового потока, узел обычно использует разделитель (например, две одинарных кавычки), чтобы обнаружить завершение сценариев. Установите этот параметр в значение NULL, если разделитель не используется для обозначения конца сценариев.  
  
 `dwFlags`  
 [in] Флаги, связанные с атрибутами текста из сценариев. Может быть сочетанием следующих значений.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Определить идентификаторы, имеющие атрибут SOURCETEXT_ATTR_IDENTIFIER и идентификации точки операторов, имеющих атрибут SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Определите текущего объекта, имеющего атрибут SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Определите строку содержимого и текст комментария, имеющего атрибут SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out size_is (`cch`)] цвет шрифта для кода сценариев.  
  
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