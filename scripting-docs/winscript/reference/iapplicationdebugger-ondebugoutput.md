---
title: "IApplicationDebugger::onDebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebugOutput
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebugOutput"
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebugOutput
Обрабатывает событие выхода отладки.  
  
## Синтаксис  
  
```  
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### Параметры  
 `pstr`  
 \[in\] строка, отображаемая в отладчике.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Отладчик обычно указывает `pstr` в окне вывода.  
  
 Этот метод вызывается при `IDebugApplication::DebugOutput` Позвонитьо.  
  
## См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)