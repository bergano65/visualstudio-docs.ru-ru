---
title: 'Иактивескриптдебуг:: Жетскриптлеттекстаттрибутес | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a5dd9e219e51b001659225636396fe45ac815b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572812"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Возвращает атрибуты текста для произвольного скриптлет.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 окне Текст скриптлет. Эта строка не должна завершаться нулем.  
  
 `uNumCodeChars`  
 окне Число символов в тексте скриптлет.  
  
 `pstrDelimiter`  
 окне Адрес разделителя конца скриптлет. Когда `pstrCode` анализируется из потока текста, узел обычно использует разделитель, например две одинарные кавычки (' '), для обнаружения конца скриптлет. Этот параметр задает разделитель, используемый узлом, позволяя обработчику скриптов предоставить некоторую условную предварительную обработку примитивов (например, заменить одинарную кавычку ['] двумя одинарными кавычками для использования в качестве разделителя). Точно то, как (и если) обработчик скриптов использует эти сведения, зависит от обработчика скриптов. Присвойте этому параметру значение NULL, если узел не использовал разделитель для обозначения конца скриптлет.  
  
 `dwFlags`  
 окне Флаги, связанные с скриптлет. Может быть сочетанием следующих значений:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Указывает, что идентификаторы и операторы точек должны быть идентифицированы с помощью флагов SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP соответственно.|  
|GETATTRFLAG_THIS|0x0100|Указывает, что идентификатор для текущего объекта должен быть идентифицирован с помощью флага SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Указывает, что содержимое строки и текст комментария должны быть идентифицированы с помощью флага SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [вход, выход] Буфер для хранения возвращаемых атрибутов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Направляющий узел, реализующий интерфейс `IDebugDocumentText`, может использовать этот метод для делегирования вызовов методу `IDebugDocumentText::GetText`.  
  
 Этот вызов предоставляется потому, что сценарии, как правило, являются выражениями и могут иметь другой синтаксис, чем блок скрипта. Если они имеют одинаковый синтаксис, реализация этого метода будет идентична реализации метода `GetScriptTextAttributes`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптдебуг](../../winscript/reference/iactivescriptdebug-interface.md)  
 [Иактивескриптдебуг:: жетскрипттекстаттрибутес](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)    
 @No__t_1 [интерфейса идебугдокументтекст](../../winscript/reference/idebugdocumenttext-interface.md)  
 @No__t_1 [идебугдокументтекст:: GetText](../../winscript/reference/idebugdocumenttext-gettext.md)  
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)