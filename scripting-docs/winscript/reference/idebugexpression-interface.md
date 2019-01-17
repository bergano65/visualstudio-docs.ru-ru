---
title: Интерфейс IDebugExpression | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9684253343aa83cf95f7d816781705eab7fbc327
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345522"
---
# <a name="idebugexpression-interface"></a>Интерфейс IDebugExpression
Представляет асинхронно вычисляемое выражение. Этот интерфейс обычно реализуется обработчиков сценариев. Интегрированная среда разработки отладчика обычно использует этот интерфейс для включения в окне немедленное выполнение или окно контрольных значений.  
  
> [!NOTE]
>  `IDebugExpression` Интерфейс доступен только из кадра стека.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugExpression` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Начинается вычисление выражения.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Прерывает выражение.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Определяет, если операция будет завершена.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Возвращает результат вычисления выражения в виде строки, а возвращаемое значение операции.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Возвращает результат вычисления выражения, как свойство отладки и возвращаемое значение операции.|