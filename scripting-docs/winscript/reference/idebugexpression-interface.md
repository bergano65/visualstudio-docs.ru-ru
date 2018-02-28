---
title: "Интерфейс IDebugExpression | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpression-interface"></a>Интерфейс IDebugExpression
Представляет асинхронно вычисленных выражений. Обработчики скриптов обычно реализуют этот интерфейс. Отладчик интегрированной среды разработки обычно использует этот интерфейс для включения немедленное выполнение окно или окно контрольных значений.  
  
> [!NOTE]
>  `IDebugExpression` Интерфейс доступен только из кадра стека.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugExpression` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Начинает вычисления выражения.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Прерывает выражение.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Определяет, если операция будет завершена.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Возвращает результат вычисления выражения, как строка и возвращаемое значение операции.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Возвращает результат вычисления выражения, как свойство отладки и возвращаемое значение операции.|