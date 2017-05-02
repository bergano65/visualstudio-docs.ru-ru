---
title: "Интерфейс IDebugAsyncOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugAsyncOperation — интерфейс"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugAsyncOperation
Диспетчер процесса отладки реализует интерфейс `IDebugAsyncOperation`.  Обработчик языка вызывает метод `IDebugApplication::CreateAsyncDebugOperation` для получения ссылки к этому интерфейсу.  Обработчик языка может использовать интерфейс `IDebugAsyncOperation`, чтобы предоставить асинхронный доступ к синхронному операции отладки.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugAsyncOperation` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Возвращает синхронные операции отладки, связанная с этим объектом.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Вызывает асинхронную операцию запуска.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Отменяет операцию.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Определяет, если операция отладка завершена.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Содержит возвращаемое значение и параметр объекта передачи синхронной операции из отладки.|