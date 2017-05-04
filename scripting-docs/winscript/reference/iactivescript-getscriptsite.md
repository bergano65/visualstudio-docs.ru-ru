---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
Извлекает объект сайта, связанный с обработчиком скрипта Windows.  
  
## Синтаксис  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### Параметры  
 `iid`  
 \[in\] идентификатор запрошенного интерфейса.  
  
 `ppvSiteObject`  
 \[out\] адрес расположения, получающей указатель интерфейса на объект сайта основного приложения.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_NOINTERFACE`|Указанный интерфейс не поддерживается.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`S_FALSE`|Нет сайт не был установлен. параметр `ppvSiteObject` ему присваивается `NULL`.|  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)