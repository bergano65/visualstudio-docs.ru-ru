---
title: "Интерфейс IDebugExpression | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression — интерфейс"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugExpression
Представляет оцененное выражение в асинхронном режиме.  Обработчики скриптов, как правило, реализуют данный интерфейс.  Интегрированная среда разработки отладчика обычно использует этот интерфейс для включения окно интерпретация выполнения или окно контрольных значений.  
  
> [!NOTE]
>  Интерфейс `IDebugExpression` доступен только из кадра стека.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugExpression` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Начинает оценку выражения.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Прерывает выражение.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Определяет, если операция завершена.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Возвращает результат оценки выражений в виде строки, а возвращаемое значение операции.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Возвращает результат оценки выражений в качестве свойства отладки и возвращаемое значение операции.|