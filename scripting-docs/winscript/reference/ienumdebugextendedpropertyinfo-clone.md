---
title: "IEnumDebugExtendedPropertyInfo::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Clone"
ms.assetid: dd645cf6-bfb3-486c-829e-bb91a6639665
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Clone
Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## Синтаксис  
  
```  
HRESULT Clone (  
   IEnumDebugExtendedPropertyInfo** ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] Возвращает клонированный интерфейс `IEnumDebugExtendedPropertyInfo`.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## См. также  
 [Интерфейс IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)