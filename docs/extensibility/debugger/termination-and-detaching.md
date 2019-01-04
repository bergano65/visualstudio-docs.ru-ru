---
title: Завершение и отсоединение | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa26d994418d411bfccc5279e9eb6bf84a8a2772
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934642"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
В следующем разделе описаны нормальное завершение.  
  
## <a name="discussion"></a>Обсуждение  
 После [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) интерфейса продолжается, если отсутствуют точки останова, исключения, ошибки времени выполнения или бесконечных циклов в приложении для отладки, Отлаживаемая программа выполняется до завершения. Это нормальное завершение.  
  
 Необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) для реализации нормальное завершение. Нормальное завершение требуется выполнить [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)