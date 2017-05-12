---
title: "IDebugFormatter::GetStringForVariant | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVariant"
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVariant
Возвращает строку, представляющую заданную ДРУГОЕ значение.  
  
## Синтаксис  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### Параметры  
 `pvar`  
 \[in\] ВЕРСИЯ, которые необходимо представить в виде строки.  
  
 `nRadix`  
 \[in\] корневой каталог, используемый для числовых значений.  
  
 `pbstrValue`  
 \[out\] строка `pvar`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает строку, представляющую заданную другое значение.  
  
## См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)