---
title: Управление выполнением и состоянием оценки | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d306ffe484605a081afa81afdcdcaa1a70339c84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098177"
---
# <a name="execution-control-and-state-evaluation"></a>Управление выполнением и состоянием оценки
Отладка приложения требуется реализовать выполнения управления шаг с заходом в функции, остановки в точках останова и продолжение выполнения. Базовые типы отладки Visual Studio его управление выполнением на события обмениваются компоненты отладчика.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Элемент управления программой](../../extensibility/debugger/program-control.md)  
 Следующие подпрограммы, которые производятся на уровне программы перечислены: Установка следующего оператора, выполнения, пошаговое выполнение, продолжение, приостановка и возобновление работы.  
  
 [Методы, связанные с точкой останова](../../extensibility/debugger/breakpoint-related-methods.md)  
 Определяет границу и ожидающие вида точек останова, которые поддерживает Visual Studio.  
  
 [Анализ стека вызова](../../extensibility/debugger/call-stack-evaluation.md)  
 Описывает методы, позволяющие просмотра кадров стека, стека вызовов во время режима приостановки реализации.  
  
 [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Объясняется, как модуль отладки (DE), диспетчер отладочной выражения вычисления (EE) и сеанса участвуют синтаксического разбора и вычисление выражения, введенные в одно из окон интегрированной среды разработки.  
  
 [События элементов управления](../../extensibility/debugger/control-events.md)  
 Описывает интерфейс, используемый для отправки событий во время выполнения управляемой программы.