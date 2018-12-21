---
title: Код контекста | Документация Майкрософт
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
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c9bdd138fbbfb4eea29004db5eb1e92814bdfec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753656"
---
# <a name="code-context"></a>Контекст кода
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, **контекст кода**:  
  
-   Предоставляет краткое описание позиции в коде, как оно известно в модуль отладки (DE). Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в потоке инструкций программы. Для нетрадиционных языков, где код не представлены инструкции, контекст кода может быть представлен либо иным образом.  
  
-   Описывает текущую позицию в потоке выполнение отлаживаемой программы.  
  
-   Существует только тогда, когда программа остановлена в точке останова.  
  
-   Имеет контекст связанный документ.  
  
-   Реализуется [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Контекст документа](../../extensibility/debugger/document-context.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)

