---
title: "Интерфейс IMachineDebugManagerEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerEvents — интерфейс"
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IMachineDebugManagerEvents
Изменения списка вводимых значений в выполняющемся поддерживаемом отладки приложения на компьютере диспетчера.  Этот интерфейс может использоваться интегрированной средой разработки отладчика для отображения динамического списка приложений.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IMachineDebugManagerEvents` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Обрабатывает событие, когда приложение добавитьо с выполняющимся список приложения.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Обрабатывает событие, когда приложение удалитьо из выполняющегося списка приложения.|