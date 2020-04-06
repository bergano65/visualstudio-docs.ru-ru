---
title: Концепции дебукера Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738981"
---
# <a name="debugger-concepts"></a>Концепции debugger
Чтобы построить пакет Visual Studio, необходимо ознакомиться с архитектурными концепциями, используемыми при проектировании пакета.

## <a name="in-this-section"></a>В этом разделе
 [Сеанс отжуражая](../../extensibility/debugger/debug-session.md) Объясняет роль сеанса в архитектуре отладки.

 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md) Определяет, что такое сервер с точки зрения отладки архитектуры, как абстрактным, так и физическим термином.

 [Поставщики портов](../../extensibility/debugger/port-suppliers.md) Определяет, что такое поставщик порта с точки зрения отладки архитектуры.

 [Порты](../../extensibility/debugger/ports.md) Определяет, что такое порт с точки зрения отладки архитектуры.

 [Процессы](../../extensibility/debugger/processes.md) Определяет, что представляет собой процесс с точки зрения отладки архитектуры.

 [Узлы программы](../../extensibility/debugger/program-nodes.md) Определяет узлы программы с точки зрения отладки архитектуры, включая то, как он может идентифицировать себя и процесс, в который он работает.

 [Программы](../../extensibility/debugger/programs.md) Определяет программу с точки зрения отладки архитектуры.

 [Темы](../../extensibility/debugger/threads.md) Определяет характеристики потоков с точки зрения отладки архитектуры.

 [Стек кадры](../../extensibility/debugger/stack-frames.md) Определяет кадр стека с точки зрения отладки архитектуры. Кадр стека — это абстракция стека, обеспечивающая контекст выполнения потока.

 [Модули](../../extensibility/debugger/modules.md) Определяет модуль с точки зрения отладки архитектуры как физический контейнер кода, например, исполняемый файл или DLL.

 [Точки разрыва](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Определяет три типа точек разрыва — ожидающих, связанных и ошибок — с точки зрения отладки архитектуры.

## <a name="related-sections"></a>См. также
 [Контексты debugger](../../extensibility/debugger/debugger-contexts.md) Объясняет, как отладка двигателя (DE) работает одновременно в контексте кода, документации и оценки выражения. Описывает для каждого из трех контекстов место, положение или оценку, относящуюся к нему.

 [Компоненты debugger](../../extensibility/debugger/debugger-components.md) Предоставляет обзор компонентов visual Studio Debugging, которые включают движок отладки (DE), оценщик выражения (EE) и обработчик символов (SH).

 [Задачи дебуза](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и оценка выражений.
