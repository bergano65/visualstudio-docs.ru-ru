---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
Анализирует процедура кода добавляет текст процедуры кода к скрипту создание обработчика и создает объект `IScriptEntry`, который соответствует процедуре кода.  
  
## Синтаксис  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### Параметры  
 `pszCode`  
 \[in\] текст скрипта, который необходимо проанализировать.  
  
 `pszFormalParams`  
 \[in\] адрес имен формальных параметров для процедуры.  Имена параметров должны быть разделены соответствующими разделителями для создания обработчика скриптов.  Имена не должны быть заключены в скобки.  
  
 `pszProcedureName`  
 \[in\] адрес имя процедуры, которое необходимо проанализировать.  
  
 `pszItemName`  
 \[in\] адрес буфера, содержащий имя элемента, связанное с объектом `IScriptEntry`.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \- скрипт\- блока.  При `pszCode` анализироватьо из потока текста, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец блока скрипта.  Установите этот параметр в значение null, если разделитель для обозначения конца блока скрипта.  
  
 `dwCookie`  
 \[in\] приложение\- указанное значение, сопоставитьо с новым объектом `IScriptEntry`.  
  
 `dwFlags`  
 \[in\] Не используется.  
  
 `pdispFor`  
 \[in\] Не используется.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Текущий обработчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] не реализует этот метод.  
  
## См. также  
 [Интерфейс IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)