---
title: Код контекста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11554be1411e63c97c8afde7cc3a819486e862ac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351330"
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