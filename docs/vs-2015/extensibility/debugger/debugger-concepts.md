---
title: 'Отладчик: основные понятия | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f8dd5567fb21fafbac3c63b84dae1e0e33b0b91
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994362"
---
# <a name="debugger-concepts"></a>Отладчик: основные понятия
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы создать на основе пакета отладки Visual Studio, необходимо уметь работать с архитектурные понятия, используемые при разработке пакета.  
  
## <a name="in-this-section"></a>В этом разделе  
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
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.
