---
title: Интерфейс IDebugStackFrame | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727534"
---
# <a name="idebugstackframe-interface"></a>Интерфейс IDebugStackFrame
Представляет кадр логического стека в стеке потока. Вызовите `IDebugStackFrame::QueryInterface` метод, чтобы получить `IDebugExpressionContext` интерфейс, который позволяет выражения вычисления» и «Контрольное windows.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugStackFrame` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Возвращает текущий контекст кода, связанный с этим кадром стека.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Возвращает описание короткие и длинные текстовые кадра стека.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Возвращает короткое или долго текстовое описание языка.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Возвращает поток, связанный с данным кадром стека.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Возвращает обозреватель свойств для текущего кадра.|