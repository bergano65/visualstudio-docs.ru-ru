---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
Перемещение окно отладки документ, содержащий заданный в верхнюю часть пользовательского интерфейса отладчика.  
  
## Синтаксис  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### Параметры  
 `pddt`  
 \[in\] отладка документ для переноса в верхнюю часть пользовательского интерфейса отладчика.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_INVALIDARG`|Документ не известен.|  
  
## Заметки  
 Данный конкретный метод вводит окно, содержащий отладочные документ в верхней части пользовательского интерфейса отладчика.  
  
## См. также  
 [Интерфейс IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)