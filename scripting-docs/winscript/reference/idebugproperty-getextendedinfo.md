---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
Получает расширенные сведения для свойства.  
  
## Синтаксис  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### Параметры  
 `cInfos`  
 \[in\] количество расширенного сведения возражает.  
  
 `rgguidExtendedInfo`  
 \[in\] массив объектов `GUID` передается таким образом, что несколько элементов расширенного сведения можно получить одновременно.  
  
 `pExtendedInfo`  
 \[out\] возвращает массив `VARIANT` s, который можно использовать для получения сведений о расширенного свойства.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## Заметки  
 Этот интерфейс возвращает подробные данные для этого объекта.  API существует только для получения сведений, не одалживает к быть восстановлены с помощью `IDebugProperty::GetPropertyInfo`\).  
  
## См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)