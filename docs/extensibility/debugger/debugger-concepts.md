---
title: 'Отладчик: основные понятия | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca5beb3d3a1ebffe33b8bcf2d7c1e4d546dd1ba1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976580"
---
# <a name="debugger-concepts"></a>Отладчик: основные понятия
Чтобы создать на основе пакета отладки Visual Studio, необходимо уметь работать с архитектурные понятия, используемые при разработке пакета.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Сеанс отладки](../../extensibility/debugger/debug-session.md)  
 Поясняется в сеансе отладки архитектуры.  
  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Определяет какой сервер является с точки зрения отладки архитектуры, в терминах абстрактные и физический.  
  
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)  
 Определяет, какое поставщика порта — с точки зрения отладки архитектуры.  
  
 [Порты](../../extensibility/debugger/ports.md)  
 Определяет какие порт — с точки зрения отладки архитектуры.  
  
 [Процессы](../../extensibility/debugger/processes.md)  
 Определяет какие процесс — это с точки зрения отладки архитектуры.  
  
 [Узлы программы](../../extensibility/debugger/program-nodes.md)  
 Определяет узел с точки зрения отладки архитектуры, в том числе как он позволяет идентифицировать себя и процесс, в котором он выполняется в программе.  
  
 [Программы](../../extensibility/debugger/programs.md)  
 Определяет программу с точки зрения отладки архитектуры.  
  
 [Потоки](../../extensibility/debugger/threads.md)  
 Определяет характеристики потоков с точки зрения архитектуры отладки.  
  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)  
 Определяет кадр стека с точки зрения отладки архитектуры. Кадр стека — это абстрактное представление стека, предоставляет контекст выполнения потока.  
  
 [Модули](../../extensibility/debugger/modules.md)  
 Определяет модуль, с точки зрения отладки архитектуры, в качестве физического контейнера кода, например исполняемый файл или библиотеку DLL.  
  
 [Точки останова](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Определяет три вида точек останова — ожидание "," граница "и" error — с точки зрения отладки архитектуры.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как модуль отладки (DE) действует одновременно в пределах кода, документацию и контекстов вычисления выражения. Описание для каждого из трех контекстов, расположение, положения или оценки, относящиеся к его.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Обзор компонентов Отладка в Visual Studio, которые включают модуль отладки (DE), средство оценки выражений (EE) и символ обработчик (SH).  
  
 [Отладка задач](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.