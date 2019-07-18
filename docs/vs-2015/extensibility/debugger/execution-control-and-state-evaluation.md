---
title: Управление выполнением и анализ состояния | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6476c925f37d70ab45bae129a8b8a379ee519c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152772"
---
# <a name="execution-control-and-state-evaluation"></a>Элемент управления выполнением и анализ состояния
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладка приложения требует внедрения таких функций управления выполнения как шаг с заходом в функции, остановки в точках останова и продолжение выполнения. Visual Studio, отладка баз его выполнения элемента управления, на события обмениваются компоненты отладчика.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Элемент управления программой](../../extensibility/debugger/program-control.md)  
 Перечисляет следующие подпрограммы, которые встречаются на уровне программы: Установка следующего оператора, выполнения, пошаговое выполнение, продолжение, приостановка и возобновление.  
  
 [Методы, связанные с точкой останова](../../extensibility/debugger/breakpoint-related-methods.md)  
 Определяет границу и ожидающих типы точек останова, которые поддерживает Visual Studio.  
  
 [Анализ стека вызова](../../extensibility/debugger/call-stack-evaluation.md)  
 Обсуждается реализация методов, которые позволяют просматривать список кадров стека, стека вызовов в режиме приостановки выполнения.  
  
 [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Объясняет, как отладчик (DE), диспетчер выражение оценки (EE) и сеанс отладки используются для синтаксического анализа, и вычисление выражения, введенные в одно из окон интегрированной среды разработки.  
  
 [События элементов управления](../../extensibility/debugger/control-events.md)  
 Описывает интерфейс, используемый для отправки событий во время выполнения управляемой программы.
