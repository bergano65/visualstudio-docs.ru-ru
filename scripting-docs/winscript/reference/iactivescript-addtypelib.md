---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
Добавляет библиотеки типов в пространстве имен для скрипта.  Это аналогично директиве `#include` на C\/C\+\+.  Он позволяет набор стандартных элементов определения класса, `typedefs` и именованные константы, добавляемый к доступному среды выполнения к скрипту.  
  
## Синтаксис  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### Параметры  
 `guidTypeLib`  
 \[in\] идентификатор CLSID библиотеки типов для добавления.  
  
 `dwMaj`  
 \[in\] основной номер версии.  
  
 `dwMin`  
 \[in\] дополнительный номер версии.  
  
 `dwFlags`  
 \[in\] флаги параметров.  Может быть следующее:  
  
|Значение|Значение|  
|--------------|--------------|  
|SCRIPTTYPELIB\_ISCONTROL|Библиотеки типов описывают элементы управления ActiveX, используемый основным приложением.|  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\).|  
|`TYPE_E_CANTLOADLIBRARY`|Библиотека указанного типа не удалось загрузить.|  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)