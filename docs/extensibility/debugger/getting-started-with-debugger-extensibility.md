---
title: Начало работы с Extensibility Debugger (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738591"
---
# <a name="get-started-with-debugger-extensibility"></a>Начало работы с разладом
Предоставляет [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] информацию, необходимую для создания и настройки компонентов отладчика, используемых для отладки программ из среды. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]отладка добавила улучшений, полученных в результате [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обширного тестирования удобства использования, выполненного на предыдущих отладчиках. Отладка [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно использовать для прохождения многоязычного приложения, или можно реализовать редактирование переменных на лету при отладке приложений и многоязычных решений.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]отладка выполняется вне процесса с отладкой программы и поэтому менее интрузивна в пространстве процесса приложения. Следовательно, проще писать компоненты, которые взаимодействуют с отладчиком, не влияя на программу отладки.

 Чтобы наилучшим [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]образом использовать, вы должны быть знакомы со следующими элементами:

- Интегрированная [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среда разработки (IDE)

- Язык программирования СЗЗ

- ATL COM

## <a name="in-this-section"></a>В этом разделе
 [Дорожная карта для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Очертания процесса реализации отладки в продукте, в зависимости от компилятора и его вывода.

 [Компоненты debugger](../../extensibility/debugger/debugger-components.md) Обеспечивает обзор компонентов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, которые включают движок отладки (DE), оценщик выражения (EE) и обработчик символов (SH).

 [Концепции debugger](../../extensibility/debugger/debugger-concepts.md) Описывает основные архитектурные концепции отладки.

 [Контексты debugger](../../extensibility/debugger/debugger-contexts.md) Объясняет, как отладка двигателя (DE) работает одновременно в контексте кода, документации и оценки выражения. Описывает для каждого из трех контекстов место, положение или оценку, относящуюся к нему.

 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и оценка выражений.
