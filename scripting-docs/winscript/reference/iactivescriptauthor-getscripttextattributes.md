---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
Возвращает атрибуты текста для блока скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### Параметры  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] Текст блока скрипта.  Эта строка должна быть завершена нулевыми.  
  
 `cch`  
 \[in\] размер, используемый для параметров `pszCode` и `pattr`.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \-\- скрипта.  При `pszCode` анализироватьо из потока текста, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец сценария.  Установите этот параметр в значение null, если разделитель, чтобы указать конец блока скрипта.  
  
 `dwFlags`  
 \[in\] флаги, которые сопоставитьы с атрибутами текст блока скрипта.  Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Укажите идентификаторы, которые имеют атрибут SOURCETEXT\_ATTR\_IDENTIFIER и укажите операторы эллипсы, имеющих атрибут SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Укажите текущий объект, имеющий атрибут SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Определение содержимого строки и текст комментария, который имеет атрибут SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out, size\_is \(`cch`\)\] Данные о цвете для кода блока скрипта.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Перечисление SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)