---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
Перечисляет членов свойства.  
  
## Синтаксис  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Параметры  
 `dwFieldSpec`  
 \[in\] определяет константы, определяющие `DBGPROP_INFO_FLAGS`, перечисленные в отладочной полям структуры свойства заполняемым.  
  
 `nRadix`  
 \[in\] корневой каталог, используемый при интерпретации любое числовое сведения.  
  
 `refiid`  
 \[in\] идентификатор IID этого передается для фильтрации перечислитель.  Идентификатор IID один из интерфейсов `IDebugPropertyEnumType`, наследующие от `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 \[out\] возвращает интерфейс `IEnumDebugPropertyInfo`, который перечисляет свойства элемента.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Интерфейс IDebugPropertyEnumType\_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)