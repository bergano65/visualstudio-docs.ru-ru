---
title: Интерфейс IDebugStackFrame | Документация Майкрософт
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
ms.openlocfilehash: 0834abbedf88b911dd952c1f3928c5da3414abec
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348546"
---
# <a name="idebugstackframe-interface"></a>Интерфейс IDebugStackFrame
Представляет логический кадр стека в стеке потоков. Вызовите `IDebugStackFrame::QueryInterface` метод, чтобы получить `IDebugExpressionContext` интерфейс, который разрешает выражение, вычисление и окна контрольных значений.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugStackFrame` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Возвращает текущий контекст кода, связанный с этим кадром стека.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Возвращает короткое или долго текстовое описание кадра стека.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Возвращает короткое или долго текстовое описание языка.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Возвращает поток, связанный с данным кадром стека.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Возвращает браузер свойств для текущего кадра.|