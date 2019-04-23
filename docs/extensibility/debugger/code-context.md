---
title: Код контекста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b02d5697260a9b212029ce1db4b7edb22de34c4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038923"
---
# <a name="code-context"></a>Контекст кода
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, **контекст кода**:

- Предоставляет краткое описание позиции в коде, как оно известно в модуль отладки (DE). Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в потоке инструкций программы. Для нетрадиционных языков, где код не представлены инструкции, контекст кода может быть представлен либо иным образом.

- Описание текущей позиции в потоке выполнения программы, которую отлаживаемым.

- Существует только тогда, когда программа остановлена в точке останова.

- Имеет контекст связанный документ.

- Реализуется [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) интерфейс.

## <a name="see-also"></a>См. также
- [Контекст документа](../../extensibility/debugger/document-context.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)