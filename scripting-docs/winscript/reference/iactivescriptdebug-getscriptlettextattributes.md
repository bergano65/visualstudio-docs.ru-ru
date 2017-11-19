---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Возвращает атрибуты текста для произвольного сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Текст сценариев. Эта строка может не заканчивается на null.  
  
 `uNumCodeChars`  
 [in] Число символов в тексте сценариев.  
  
 `pstrDelimiter`  
 [in] Адрес разделитель end из сценариев. Когда `pstrCode` анализируется из текстового потока, узел обычно использует разделители, такие как двумя одинарными кавычками («), чтобы определить конец сценариев. Этот параметр определяет разделитель, который используется узел, позволяя обработчик скриптов для предоставления некоторых условного примитивов предварительной обработки (например, замените одинарная кавычка ['] две одинарные кавычки для использования в качестве разделителя). Как именно (и если) сценария подсистемой этих сведений зависит от обработчика скриптов. Установите этот параметр в значение NULL, если узел не использовали разделитель для обозначения конца сценариев.  
  
 `dwFlags`  
 [in] Флаги, связанные с помощью сценариев. Может представлять собой сочетание этих значений:  
  
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
  
 Этот вызов предоставляется, поскольку сценарии, как правило, выражения и может иметь различный синтаксис, чем блок сценария. Если они имеют тот же синтаксис, реализация этого метода будет идентична реализация `GetScriptTextAttributes` метода.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)