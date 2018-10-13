---
title: Завершение и отсоединение | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb6705c1189649b986776b99cd105f1e9532e160
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305335"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается нормальное завершение.  
  
## <a name="discussion"></a>Обсуждение  
 После [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) интерфейса продолжается, если отсутствуют точки останова, исключения, ошибки времени выполнения или бесконечных циклов в приложении для отладки, Отлаживаемая программа будет выполняться до завершения. Это нормальное завершение.  
  
 Необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) для реализации нормальное завершение. Это требует внедрения [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)

