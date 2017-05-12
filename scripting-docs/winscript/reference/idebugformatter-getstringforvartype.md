---
title: "IDebugFormatter::GetStringForVarType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVarType"
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVarType
Возвращает строку, которая представляет заданное значение VARTYPE.  
  
## Синтаксис  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### Параметры  
 `vt`  
 \[in\] VARTYPE, которые необходимо представить в виде строки.  
  
 `ptdescArrayType`  
 \[in\] массив структур, который описывает типы.  
  
 `pbstr`  
 \[out\] строка `vt`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Метод возвращает строку, которая представляет заданное значение VARTYPE.  
  
## См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)