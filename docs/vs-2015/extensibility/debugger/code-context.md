---
title: Контекст кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197376"
---
# <a name="code-context"></a>Контекст кода
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладке — **контекст кода**:  
  
- Предоставляет абстракцию места в коде, известное модулю отладки (DE). В настоящее время для большинства архитектур времени выполнения контекст кода можно рассматривать как адрес в потоке инструкций программы. Для нетрадиционных языков, где код может не быть представлен инструкциями, контекст кода может быть представлен другими средствами.  
  
- Описывает текущую точку в потоке выполнения отлаживаемой программы.  
  
- Существует только в том случае, если программа остановлена в точке останова.  
  
- Имеет связанный контекст документа.  
  
- Реализуется с помощью интерфейса [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## <a name="see-also"></a>См. также:  
 [Контекст документа](../../extensibility/debugger/document-context.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
