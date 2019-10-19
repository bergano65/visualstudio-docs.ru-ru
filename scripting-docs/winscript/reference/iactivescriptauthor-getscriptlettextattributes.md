---
title: 'Иактивескриптаусор:: Жетскриптлеттекстаттрибутес | Документация Майкрософт'
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
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576171"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Возвращает атрибуты текста объекта скриптлет.  
  
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
 [in, size_is (`cch`)] Текст скриптлет. Эта строка не должна завершаться нулем.  
  
 `cch`  
 окне Размер, используемый для параметров `pszCode` и `pattr`.  
  
 `pszDelimiter`  
 окне Адрес разделителя конца скриптлета. При синтаксическом анализе `pszCode` из потока текста хост обычно использует разделитель (например, две одинарные кавычки) для обнаружения конца скриптлет. Присвойте этому параметру значение NULL, если для обнаружения конца скриптлет не используется разделитель.  
  
 `dwFlags`  
 окне Флаги, связанные с атрибутами Text объекта скриптлет. Может быть сочетанием следующих значений.  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Выявление идентификаторов, имеющих атрибут SOURCETEXT_ATTR_IDENTIFIER, и идентификации операторов Dot, имеющих атрибут SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Определяет текущий объект, имеющий атрибут SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Выявление строкового содержимого и текста комментария с атрибутом SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Сведения о цвете для кода скриптлет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Иактивескриптаусор:: жетскрипттекстаттрибутес](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)    
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)