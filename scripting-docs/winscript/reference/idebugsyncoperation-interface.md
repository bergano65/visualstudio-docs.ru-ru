---
title: "Интерфейс IDebugSyncOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSyncOperation — интерфейс"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugSyncOperation
Позволяет обработчику скриптов для резюмировать операцию \(например вычисление выражений будут выполняться, пока\), выдающую гнездить в частности блокировать поток.  Интерфейс также предоставляет механизм отмены безответные операции.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugSyncOperation` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Возвращает поток приложения целевого объекта для синхронной операции.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Синхронно выполняет операцию и возвращает значение.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Отменяет хода выполнения операции в другом потоке.|