---
title: Концепции отладчика | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738981"
---
# <a name="debugger-concepts"></a>Основные понятия отладчика
Для создания пакета отладки Visual Studio необходимо ознакомиться с концепциями архитектуры, используемыми при проектировании пакета.

## <a name="in-this-section"></a>В этом разделе
 [Сеанс отладки](../../extensibility/debugger/debug-session.md) Объясняет роль сеанса в архитектуре отладки.

 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md) Определяет, что представляет собой сервер в контексте архитектуры отладки, как абстрактные, так и физические термины.

 [Поставщики портов](../../extensibility/debugger/port-suppliers.md) Определяет, что представляет собой поставщик порта в контексте архитектуры отладки.

 [Порты](../../extensibility/debugger/ports.md) Определяет, что представляет собой порт в контексте архитектуры отладки.

 [Процессы](../../extensibility/debugger/processes.md) Определяет, что такое процесс в контексте архитектуры отладки.

 [Узлы программы](../../extensibility/debugger/program-nodes.md) Определяет узел программы с точки зрения архитектуры отладки, включая то, как он может идентифицировать себя и процесс, в котором он выполняется.

 [Программы](../../extensibility/debugger/programs.md) Определяет программу с точки зрения архитектуры отладки.

 [Потоки](../../extensibility/debugger/threads.md) Определяет характеристики потоков с точки зрения архитектуры отладки.

 [Кадры стека](../../extensibility/debugger/stack-frames.md) Определяет кадр стека с точки зрения архитектуры отладки. Кадр стека — это абстракция стека, предоставляющего контекст выполнения потока.

 [Модули](../../extensibility/debugger/modules.md) Определяет модуль с точки зрения архитектуры отладки в качестве физического контейнера кода, например исполняемого файла или библиотеки DLL.

 [Точки останова](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Определяет три типа точек останова: ожидание, привязка и ошибка — с точки зрения архитектуры отладки.

## <a name="related-sections"></a>Связанные разделы
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md) Объясняет, как подсистема отладки (DE) работает одновременно в рамках кода, документации и контекстов оценки выражений. Описывает, для каждого из трех контекстов: расположение, положение или вычисление, относящиеся к нему.

 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md) Содержит общие сведения о компонентах отладки Visual Studio, включая модуль отладки (DE), средство оценки выражений (EE) и обработчик символов (SH).

 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md) Содержит ссылки на различные задачи отладки, такие как запуск программы и вычисление выражений.
