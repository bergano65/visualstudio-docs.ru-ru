---
title: "IDebugProperty::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetPropertyInfo"
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetPropertyInfo
Возвращает значение `IDebugProperty`, описывающий метод или индексированное свойство.  
  
## Синтаксис  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGS dwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### Параметры  
 `dwFields`  
 \[in\] определяет константы `DBGPROP_INFO_FLAGS`, определяющие поля, которое нужно заполнять в структуре `DebugPropertyInfo`.  
  
 `nRadix`  
 \[in\] корневой каталог, используемый в отформатировать любое числовое сведения.  
  
 `pPropertyInfo`  
 \[out\] возвращает структуру `DebugPropertyInfo`, описывающая свойства.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)