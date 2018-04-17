---
title: Контекст кода | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="code-context"></a>Контекст кода
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка, **контекст кода**:  
  
-   Предоставляет краткое описание позиции в коде, как оно известно в модуль отладки (DE). Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в поток инструкций программы. Контекст кода для нетрадиционных языков, где код не представлены инструкции, можно представить с помощью других средств.  
  
-   Описывает текущую позицию в потоке выполнения отлаживаемой программы.  
  
-   Существует, только когда остановлено в точке останова.  
  
-   Имеет контекст связанный документ.  
  
-   Реализуется [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Контекст документа](../../extensibility/debugger/document-context.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)