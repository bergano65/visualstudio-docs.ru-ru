---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
Извлекает код языка, связанный с пользовательским интерфейсом основного приложения.  Обработчик скриптов использует идентификатор, чтобы убедиться, что строки ошибки и другие элементы интерфейса пользователя, вызываемые обработчиком отображаются в соответствующий язык.  
  
## Синтаксис  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### Параметры  
 `plcid`  
 \[out\] адрес переменной, которая получает код языка для элементов интерфейса пользователя для указания на обработчик скриптов.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_NOTIMPL`|Этот метод не реализован.  Используйте система\- указанный языковой стандарт.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
  
## Заметки  
 Если этот метод возвращает `E_NOTIMPL`, то система\- указанный код языка должен использоваться.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)