---
title: "Интерфейс IDebugThreadCall | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall — интерфейс"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugThreadCall
Интерфейс `IDebugThreadCall` обычно реализуется компонентом, который выполняет крест\- потока с `IDebugThread` выстраивая реализацию, указанные в процессе отлаживал диспетчер \(PDM\).  
  
 PDM вызывает интерфейс `IDebugThreadCall` в нужному потоке и интерфейс `IDebugThreadCall` отправляет вызов необходимой реализации.  Интерфейс `IDebugThreadCall` приводит сведения о параметрах, переданное параметры для соответствующей верхней части.  
  
 Интерфейс `IDebugThreadCall` свободен\- продетый потоками объект.  
  
## Методы  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugThreadCall` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Обрабатывает вызовы для запуска кода в другом потоке.|