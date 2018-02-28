---
title: "IActiveScriptDebug::GetScriptTextAttributes | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8e9cd76da3e754eabce836b386893043dcd0622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Возвращает атрибуты текста для произвольного блок текста сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Блок текста сценария. Эта строка может не заканчивается на null.  
  
 `uNumCodeChars`  
 [in] Число символов в текстовом блоке скрипта.  
  
 `pstrDelimiter`  
 [in] Адрес разделитель end из скрипта блока. Когда `pstrCode` анализируется из текстового потока, узел обычно использует разделители, такие как двух одинарных кавычки («), чтобы определить конец блока скрипта. Этот параметр определяет разделитель, который используется узел, позволяя обработчик скриптов для предоставления некоторых условного примитивов предварительной обработки (например, замените одинарная кавычка ['] две одинарные кавычки для использования в качестве разделителя). Как именно (и если) сценария подсистемой этих сведений зависит от обработчика скриптов. Установите этот параметр в значение NULL, если узел не использовали разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 [in] Флаги, связанные с блоком сценария. Может представлять собой сочетание этих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Указывает, что идентификаторы и операторы точка должна быть определена с флагами SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP соответственно.|  
|GETATTRFLAG_THIS|0x0100|Указывает, что идентификатор для текущего объекта должна быть определена с флагом SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Указывает, что строка содержимого и текст комментария должна быть определена с флагом SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Буфер, содержащий возвращаемые атрибуты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Промежуточный узел, который реализует `IDebugDocumentText` интерфейса можно использовать этот метод для делегирования вызовов `IDebugDocumentText::GetText` метод.  
  
 Этот метод для блоков сценария; `GetScriptletTextAttributes` метод предназначен для сценарии.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)