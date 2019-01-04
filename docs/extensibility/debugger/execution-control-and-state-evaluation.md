---
title: Управление выполнением и анализ состояния | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 8a90f1fa098cfb60e6a3939332095dca5e52e3eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852105"
---
# <a name="execution-control-and-state-evaluation"></a>Выполнение управления и состояние оценки
Отладка приложения требует внедрения таких функций управления выполнения как шаг с заходом в функции, остановки в точках останова и продолжение выполнения. Visual Studio, отладка баз его выполнения элемента управления, на события обмениваются компоненты отладчика.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Управление программой](../../extensibility/debugger/program-control.md)  
 Перечисляет следующие подпрограммы, которые встречаются на уровне программы: Установка следующего оператора, выполнения, пошаговое выполнение, продолжение, приостановка и возобновление.  
  
 [Методы, связанные с точки останова](../../extensibility/debugger/breakpoint-related-methods.md)  
 Определяет границу и ожидающих типы точек останова, которые поддерживает Visual Studio.  
  
 [Анализ стека вызова](../../extensibility/debugger/call-stack-evaluation.md)  
 Обсуждается реализация методов, которые позволяют просматривать список кадров стека, стека вызовов в режиме приостановки выполнения.  
  
 [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Объясняет, как отладчик (DE), диспетчер выражение оценки (EE) и сеанс отладки используются для синтаксического анализа, и вычисление выражения, введенные в одно из окон интегрированной среды разработки.  
  
 [События элементов управления](../../extensibility/debugger/control-events.md)  
 Описывает интерфейс, используемый для отправки событий во время выполнения управляемой программы.