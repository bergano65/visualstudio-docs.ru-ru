---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
Извлекает интерфейс `IDispatch` для методов и свойств, связанных с выполняющийся в данный момент скриптом.  
  
## Синтаксис  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### Параметры  
 `pstrItemName`  
 \[in\] адрес буфера, содержащий имя элемента, для которого вызывающему объекту требуется связанный объект диспетчеризации.  Если этот параметр `NULL`, объект диспетчера содержащего его члены все глобальные методы и свойства, определенные скриптом.  Через интерфейс `IDispatch` и связанный с ним интерфейс `ITypeInfo`, узел может вызвать методы или представление сценария и изменять переменные скрипта.  
  
 `ppdisp`  
 \[out\] адрес переменной, которая получает указатель на объект, связанный с методами и свойствами скрипта глобальный.  Если обработчик скриптов не поддерживает такой объект, `NULL` возвращается.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\).|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчера; параметр `ppdisp` имеет значение NULL.|  
  
## Заметки  
 Поскольку методы и свойства могут быть добавитьы с помощью вызова интерфейса [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md), возвращенный интерфейс `IDispatch` этим методом может динамически поддержки новых методов и свойств.  Аналогично, метод должен возвращать `IDispatch::GetTypeInfo` новый, уникальный интерфейс `ITypeInfo`, когда методы и свойства добавитьы.  Обратите внимание, что обработчики языка не изменяются таким способом, который `IDispatch` интерфейс несовместим с предыдущими интерфейсом `ITypeInfo` вернула.  Это означает, например, что идентификаторов dispid никогда не будет повторно использоваться.  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)