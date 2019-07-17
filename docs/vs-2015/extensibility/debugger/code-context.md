---
title: Код контекста | Документация Майкрософт
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197376"
---
# <a name="code-context"></a>Контекст кода
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, **контекст кода**:  
  
- Предоставляет краткое описание позиции в коде, как оно известно в модуль отладки (DE). Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в потоке инструкций программы. Для нетрадиционных языков, где код не представлены инструкции, контекст кода может быть представлен либо иным образом.  
  
- Описывает текущую позицию в потоке выполнение отлаживаемой программы.  
  
- Существует только тогда, когда программа остановлена в точке останова.  
  
- Имеет контекст связанный документ.  
  
- Реализуется [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Контекст документа](../../extensibility/debugger/document-context.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
