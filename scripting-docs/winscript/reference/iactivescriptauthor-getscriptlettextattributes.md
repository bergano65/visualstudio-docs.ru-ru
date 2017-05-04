---
title: "IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptletTextAttributes"
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::GetScriptletTextAttributes
Возвращает атрибуты текст сценария.  
  
## Синтаксис  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### Параметры  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] Текст скрипта.  Эта строка должна быть завершена нулевыми.  
  
 `cch`  
 \[in\] размер, используемый для параметров `pszCode` и `pattr`.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \-\- скрипта.  При `pszCode` анализироватьо из потока текста, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец сценария.  Установите этот параметр в значение null, если разделитель не используется для указания конец сценария.  
  
 `dwFlags`  
 \[in\] флаги, которые сопоставитьы с атрибутами текст сценария.  Может быть сочетанием следующих значений.  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Укажите идентификаторы, которые имеют атрибут SOURCETEXT\_ATTR\_IDENTIFIER и укажите операторы эллипсы, имеющих атрибут SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Укажите текущий объект, имеющий атрибут SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Определение содержимого строки и текст комментария, который имеет атрибут SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out, size\_is \(`cch`\)\] Данные о цвете для кода скрипта.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Перечисление SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)