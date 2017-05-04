---
title: "IActiveScriptDebug::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptTextAttributes"
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptTextAttributes
Возвращает атрибуты текста для произвольного фрагмента текста скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Параметры  
 `pstrCode`  
 \[in\] текст блока скрипта.  Этой завершенной строке не требуется нулевыми.  
  
 `uNumCodeChars`  
 \[in\] количество символов в тексте блока скрипта.  
  
 `pstrDelimiter`  
 \[in\] адрес разделителя элемент \- скрипт\- блока.  При `pstrCode` анализироватьо из потока текста, основное приложение обычно использует разделитель, например 2 одинарных кавычки \("\), чтобы обнаружить конец блока скрипта.  Этот параметр задает разделитель, используемый основным приложением, что обработчик скриптов, чтобы обеспечить какую\-либо условную предобработку примитивов \(например, заменящ одинарная кавычка \('\) с 2 одинарными кавычками для использования в качестве разделителя\).  То, как \(и, если\), то обработчик скриптов использует этот зависит от информации обработчика скриптов.  Установите этот параметр в значение null, если основное приложение не использует разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 \[in\] флаги, связанные с блоком скрипта.  Может оказаться сочетание этих значений:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Указывает, что идентификаторы и операторы с многоточием должны быть определены с SOURCETEXT\_ATTR\_IDENTIFIER и SOURCETEXT\_ATTR\_MEMBERLOOKUP пометит соответственно.|  
|GETATTRFLAG\_THIS|0x0100|Указывает на то, что идентификатор для текущего объекта должен быть определен с флагом SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Указывает, что содержимое строки и текст комментария должны быть указаны с флагом SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out\] буфер, содержащий возвращаемые атрибуты.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Промежуточный узел, который реализует интерфейс `IDebugDocumentText` может использовать этот метод, чтобы делегировать вызовы метода `IDebugDocumentText::GetText`.  
  
 Этот метод для блоков скриптов; метод `GetScriptletTextAttributes` для сценария.  
  
## См. также  
 [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Перечисление SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)