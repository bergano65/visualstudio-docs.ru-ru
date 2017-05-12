---
title: "Метод IActiveScriptProfilerCallback3::SetWebWorkerId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод IActiveScriptProfilerCallback3::SetWebWorkerId
Уведомляет профилировщик о идентификатор рабочего, который будет использоваться для данного сеанса профилирования.  Если функция не выполняется в контексте страницы, этот метод не вызывается.  Значение `webWorkerId` увеличивает 1 для каждого рабочего, начиная с 1.  Значения идентификаторов не предназначены стабилизированы за сеансом и соответствуют только к порядку, в котором рабочие были создатьы.  
  
## Синтаксис  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### Параметры  
 `webWorkerId`  
 Идентификатор рабочего Интернета  
  
## Возвращаемое значение  
 Возвращаемое значение этого метода игнорироватьо обработчиком скриптов.