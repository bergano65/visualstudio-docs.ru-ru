---
title: Компоненты debugger Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739010"
---
# <a name="debugger-components"></a>Компоненты debugger
Отладчик [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] реализован как VSPackage и управляет всей сессией отладки. Сеанс отладки включает в себя следующие элементы:

- **Пакет debug:** Отладчик [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет тот же пользовательский интерфейс независимо от того, что в настоящее время отлажены.

- **Менеджер отладки сеанса (SDM):** Обеспечивает согласованный программный [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интерфейс для Debugger для управления различными двигателями отладки. Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Менеджер процесса отладки (PDM):** Управляет для всех запущенных [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]экземпляров , список всех программ, которые могут быть или в настоящее время отлажены. Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Двигатель debug (DE):** Отвечает за мониторинг отладки программы, информирование о состоянии запущенной программы до SDM и PDM, а также взаимодействие с поставщиком оценщиков выражений и символом для проведения анализа состояния памяти и переменных программы в режиме реального времени. Он реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (для языков, которые он поддерживает) и сторонними поставщиками, которые хотят поддерживать свое собственное время выполнения.

- **Оценка экспрессии (EE):** Обеспечивает поддержку динамической оценки переменных и выражений, предоставляемых пользователем, когда программа была остановлена в определенной точке. Он реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (для языков, которые он поддерживает) и сторонними поставщиками, которые хотят поддерживать свои собственные языки.

- **Поставщик символов (SP):** Также называемый обработчиком символов, отображает отладки символов программы в запущенном экземпляре программы, чтобы можно было предоставить значимую информацию (например, отладку на уровне исходного кода и оценку выражения). Он реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (для символов Общего Языка Runtime и формата символа Program DataBase) и сторонних поставщиков, которые имеют свой собственный собственный метод хранения информации об отладке.

  На следующей диаграмме показано отношение между этими элементами отладчика Visual Studio.

  ![Обзор компонентов отлады](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>В этом разделе
 [Пакет debug](../../extensibility/debugger/debug-package.md) Обсуждает пакет отладки, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] работает в оболочке и обрабатывает весь uI.

 [Менеджер процесса отладки](../../extensibility/debugger/process-debug-manager.md) Предоставляет обзор особенностей ДПМ, который является менеджером процессов, которые могут быть отдипированы.

 [Менеджер отладки сеанса](../../extensibility/debugger/session-debug-manager.md) Определяет SDM, который обеспечивает единое представление сеанса отладки в IDE. SDM управляет DE.

 [Двигатель debug](../../extensibility/debugger/debug-engine.md) Документы служб ы отладки, предоставляемые DE.

 [Режимы работы](../../extensibility/debugger/operational-modes.md) Предоставляет обзор трех режимов, в которых может работать IDE: режим проектирования, режим запуска и режим разрыва. Обсуждаются также механизмы перехода.

 [Оценка экспрессии](../../extensibility/debugger/expression-evaluator.md) Объясняет назначение EE во время выполнения.

 [Поставщик символов](../../extensibility/debugger/symbol-provider.md) Обсуждает, как при реализации поставщик символов оценивает переменные и выражения.

 [Введите визуализатор и пользовательский зритель](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Обсуждает, что такое визуализатор типа и пользовательский зритель и какую роль играет оценщик выражения в поддержке обоих.

## <a name="related-sections"></a>См. также
 [Концепции debugger](../../extensibility/debugger/debugger-concepts.md) Описывает основные архитектурные концепции отладки.

 [Контексты debugger](../../extensibility/debugger/debugger-contexts.md) Объясняет, как DE работает одновременно в контекстах оценки кода, документации и выражения. Описывает для каждого из трех контекстов место, положение или оценку, относящуюся к нему.

 [Задачи дебуза](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и оценка выражений.

## <a name="see-also"></a>См. также
- [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
