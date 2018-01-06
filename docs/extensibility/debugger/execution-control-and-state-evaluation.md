---
title: "Управление выполнением и состоянием оценки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5ebc9d78f50454a0b0576c4d339102b08cb3e26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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