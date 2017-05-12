---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
Процесс отладки уведомляет диспетчер, что обработчик языка в режиме единый\- шага собирается вернуться к своему вызывающему объекту.  
  
## Синтаксис  
  
```  
HRESULT StepOutComplete();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Обработчики языка вызывают этот метод в режиме единый\- шага непосредственно перед тем, как они возвращают к их вызывающему объекту.  Процесс отладки использования диспетчера эта возможность уведомить другие обработчики скриптов, что они должны прервать выполнение при первой возможности.  Этот метод, как режимы шага крест\- языка реализованы.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)