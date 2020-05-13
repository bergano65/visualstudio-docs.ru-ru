---
title: Контексты дебукера (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738972"
---
# <a name="debugger-contexts"></a>Контексты debugger
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке двигатель отладки (DE) работает одновременно в нескольких различных контекстах:

- Контекст кода, описывающий текущее местоположение в потоке выполнения программы.

- Контекст или позиция документации, описывающие текущее положение в исходном документе.

- Контекст оценки выражения, описывающий контекст, в котором будет проводиться оценка выражения.

## <a name="in-this-section"></a>В этом разделе
 [Контекст кода](../../extensibility/debugger/code-context.md) Обсуждает контекст кода как адрес в потоке инструкций программы в современных архитектурах времени выполнения по сравнению с нетрадиционными языками, где код может быть представлен не инструкциями, а некоторыми другими средствами.

 [Позиция документа](../../extensibility/debugger/document-position.md) Определяет позицию документа при отладке Visual Studio с помощью абстракции позиции в исходном файле, известном IDE.

 [Контекст документа](../../extensibility/debugger/document-context.md) Обсуждается, какой контекст документа представляется при отладке Visual Studio по отношению к исходной файлу. Также обсуждается, как обработчик символов отображает контекст кода в контексте документации.

 [Контекст оценки выражения](../../extensibility/debugger/expression-evaluation-context.md) Предоставляет информацию о контексте оценки выражения в Visual Studio. Например, контекст оценки выражения, связанный с кадром стека, предоставляет контекст для оценки локальных переменных, параметров метода и членов класса.

## <a name="related-sections"></a>См. также
 [Понятия debug](../../extensibility/debugger/debugger-concepts.md) Описывает основные архитектурные концепции отладки.

 [Компоненты debug](../../extensibility/debugger/debugger-components.md) Предоставляет обзор компонентов отладки Visual Studio, которые включают движок отладки (DE), оценщик выражения (EE) и обработчик символов (SH).

 [Задачи дебуза](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и оценка выражений.
