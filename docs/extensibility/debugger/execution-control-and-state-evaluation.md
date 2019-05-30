---
title: Управление выполнением и анализ состояния | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bda531e94bdea07ee37eed2b0b79e6f0667ba28e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315238"
---
# <a name="execution-control-and-state-evaluation"></a>Выполнение управления и состояние оценки
Отладка приложения требует внедрения таких функций управления выполнения как шаг с заходом в функции, остановки в точках останова и продолжение выполнения. Visual Studio, отладка баз его выполнения элемента управления, на события обмениваются компоненты отладчика.

## <a name="in-this-section"></a>Содержание раздела
 [Программы управления](../../extensibility/debugger/program-control.md) перечислены следующие подпрограммы, которые встречаются на уровне программы: Установка следующего оператора, выполнения, пошаговое выполнение, продолжение, приостановка и возобновление.

 [Методы, связанные с точки останова](../../extensibility/debugger/breakpoint-related-methods.md) определяет границу и ожидающих типы точек останова, которые поддерживает Visual Studio.

 [Анализ стека вызова](../../extensibility/debugger/call-stack-evaluation.md) обсуждается реализация методов, которые позволяют просматривать список кадров стека, стека вызовов в режиме приостановки выполнения.

 [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) объясняется, как модуль отладки (DE), вычисление выражений (EE) и диспетчер отладки сеансов применяемые для синтаксического анализа и оценки выражения, введенные в одно из окон интегрированной среды разработки.

 [Контролировать события](../../extensibility/debugger/control-events.md) описывает интерфейс, используемый для отправки событий во время выполнения управляемой программы.