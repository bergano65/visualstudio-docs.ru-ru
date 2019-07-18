---
title: Интерфейс IDebugExpression | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1757317e9ab148b508bfed95107b5c3b3369b598
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430025"
---
# <a name="idebugexpression-interface"></a>Интерфейс IDebugExpression
Представляет асинхронно вычисляемое выражение. Этот интерфейс обычно реализуется обработчиков сценариев. Интегрированная среда разработки отладчика обычно использует этот интерфейс для включения в окне немедленное выполнение или окно контрольных значений.  
  
> [!NOTE]
> `IDebugExpression` Интерфейс доступен только из кадра стека.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugExpression` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Начинается вычисление выражения.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Прерывает выражение.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Определяет, если операция будет завершена.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Возвращает результат вычисления выражения в виде строки, а возвращаемое значение операции.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Возвращает результат вычисления выражения, как свойство отладки и возвращаемое значение операции.|