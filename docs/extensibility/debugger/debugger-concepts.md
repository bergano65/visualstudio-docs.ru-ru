---
title: 'Отладчик: основные понятия | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1d9905281c83287b8b54f57a233c2056462226f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345936"
---
# <a name="debugger-concepts"></a>Отладчик: основные понятия
Чтобы создать на основе пакета отладки Visual Studio, необходимо уметь работать с архитектурные понятия, используемые при разработке пакета.

## <a name="in-this-section"></a>Содержание раздела
 [Сеанс отладки](../../extensibility/debugger/debug-session.md) поясняется в сеансе отладки архитектуры.

 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md) определяет, какой сервер является с точки зрения отладки архитектуры, в терминах абстрактные и физический.

 [Порт поставщики](../../extensibility/debugger/port-suppliers.md) определяет, какие поставщика порта — с точки зрения отладки архитектуры.

 [Порты](../../extensibility/debugger/ports.md) определяет, какой порт — с точки зрения отладки архитектуры.

 [Процессы](../../extensibility/debugger/processes.md) определяет, какой процесс — это с точки зрения отладки архитектуры.

 [Программа узлы](../../extensibility/debugger/program-nodes.md) определяет узел с точки зрения отладки архитектуры, в том числе как он позволяет идентифицировать себя и процесс выполняется в программе.

 [Программы](../../extensibility/debugger/programs.md) определяет программы с точки зрения отладки архитектуры.

 [Потоки](../../extensibility/debugger/threads.md) определяет характеристики потоков с точки зрения отладки архитектуры.

 [Кадры стека](../../extensibility/debugger/stack-frames.md) определяет кадр стека с точки зрения отладки архитектуры. Кадр стека — это абстрактное представление стека, предоставляет контекст выполнения потока.

 [Модули](../../extensibility/debugger/modules.md) определяет модуль, с точки зрения отладки архитектуры, в качестве физического контейнера кода, например исполняемый файл или библиотеку DLL.

 [Точки останова](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) определяет три вида точек останова — ожидание "," граница "и" error — с точки зрения отладки архитектуры.

## <a name="related-sections"></a>Связанные разделы
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md) объясняется, как модуль отладки (DE) работает одновременно в контекстах оценки кода, документацию и выражение. Описание для каждого из трех контекстов, расположение, положения или оценки, относящиеся к его.

 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md) представлен обзор компонентов Отладка в Visual Studio, которые включают модуль отладки (DE), средство оценки выражений (EE) и символ обработчик (SH).

 [Отладка задач](../../extensibility/debugger/debugging-tasks.md) содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.