---
title: Код контекста | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e9ff125a75731de5ca312e5417996f9c6dda764
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569446"
---
# <a name="code-context"></a>Контекст кода
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [контекст кода](https://docs.microsoft.com/visualstudio/extensibility/debugger/code-context).  
  
В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, **контекст кода**:  
  
-   Предоставляет краткое описание позиции в коде, как оно известно в модуль отладки (DE). Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в потоке инструкций программы. Для нетрадиционных языков, где код не представлены инструкции, контекст кода может быть представлен либо иным образом.  
  
-   Описывает текущую позицию в потоке выполнение отлаживаемой программы.  
  
-   Существует только тогда, когда программа остановлена в точке останова.  
  
-   Имеет контекст связанный документ.  
  
-   Реализуется [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Контекст документа](../../extensibility/debugger/document-context.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)

