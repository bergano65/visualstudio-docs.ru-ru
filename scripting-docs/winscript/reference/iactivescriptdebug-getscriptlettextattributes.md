---
title: IActiveScriptDebug::GetScriptletTextAttributes | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 757c56750ee54e7de50f245b8b643cc5983f3149
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097556"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Возвращает атрибуты текста для произвольных скриптлета.  
  
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
 [in] Текст сценария. Эта строка не обязательно нулевым байтом.  
  
 `uNumCodeChars`  
 [in] Число символов в тексте скриптлета.  
  
 `pstrDelimiter`  
 [in] Адрес end-разделителя конца скриптлета. Когда `pstrCode` анализируется из потока текста узел обычно использует разделитель, например две одинарные кавычки («), чтобы определить конец скриптлета. Этот параметр задает разделитель, используемый узлом, позволяя обработчик скриптов для предоставления некоторых условного примитивных предварительной обработки (например, замените одинарной кавычки ['] две одинарные кавычки для использования в качестве разделителя). Точный способ (и нужно ли) сценариев подсистемой, эта информация зависит от обработчика скриптов. Установите этот параметр в значение NULL, если узел не используется разделитель для обозначения конца сценария.  
  
 `dwFlags`  
 [in] Флаги, связанные со скриптлетом. Может представлять собой сочетание этих значений:  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Указывает, что идентификаторы и точка операторы должны идентифицироваться с флагами SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP, соответственно.|  
|GETATTRFLAG_THIS|0x0100|Указывает, что идентификатор для текущего объекта должна определяться с флагом SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Указывает, что строка содержимого и текст примечания должны определяться с флагом SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Буфер должен содержать возвращаемые атрибуты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Промежуточный узел, который реализует `IDebugDocumentText` интерфейс этот метод можно использовать для делегирования вызовов `IDebugDocumentText::GetText` метод.  
  
 Этот вызов предоставляется в том случае, поскольку сценарии, как правило, выражения и могут иметь различный синтаксис, чем блок сценария. Если они имеют тот же синтаксис, реализация этого метода будет совпадать с реализацией `GetScriptTextAttributes` метод.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)