---
title: 'Иактивескриптдебуг:: Жетскрипттекстаттрибутес | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576921"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Возвращает атрибуты текста для произвольного блока текста скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 окне Текст блока скрипта. Эта строка не должна завершаться нулем.  
  
 `uNumCodeChars`  
 окне Количество символов в тексте блока скрипта.  
  
 `pstrDelimiter`  
 окне Адрес разделителя-блока конца скрипта. Когда `pstrCode` анализируется из потока текста, узел обычно использует разделитель, например две одинарные кавычки (' '), для обнаружения конца блока скрипта. Этот параметр задает разделитель, используемый узлом, позволяя обработчику скриптов предоставить некоторую условную предварительную обработку примитивов (например, заменить одинарную кавычку ['] двумя одинарными кавычками для использования в качестве разделителя). Точно то, как (и если) обработчик скриптов использует эти сведения, зависит от обработчика скриптов. Присвойте этому параметру значение NULL, если узел не использовал разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 окне Флаги, связанные с блоком скрипта. Может быть сочетанием следующих значений:  
  
|постоянное значение.|Значение|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Указывает, что идентификаторы и операторы точек должны быть идентифицированы с помощью флагов SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP соответственно.|  
|GETATTRFLAG_THIS|0x0100|Указывает, что идентификатор для текущего объекта должен быть идентифицирован с помощью флага SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Указывает, что содержимое строки и текст комментария должны быть идентифицированы с помощью флага SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [вход, выход] Буфер для хранения возвращаемых атрибутов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Направляющий узел, реализующий интерфейс `IDebugDocumentText`, может использовать этот метод для делегирования вызовов методу `IDebugDocumentText::GetText`.  
  
 Этот метод для блоков сценариев; метод `GetScriptletTextAttributes` предназначен для сценарии.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса иактивескриптдебуг](../../winscript/reference/iactivescriptdebug-interface.md)  
 [Иактивескриптдебуг:: жетскриптлеттекстаттрибутес](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
   [интерфейса идебугдокументтекст](../../winscript/reference/idebugdocumenttext-interface.md)  
   [идебугдокументтекст:: GetText](../../winscript/reference/idebugdocumenttext-gettext.md)  
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)