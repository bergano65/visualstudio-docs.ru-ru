---
title: Управление выполнением и оценка состояния | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152772"
---
# <a name="execution-control-and-state-evaluation"></a>Элемент управления выполнением и анализ состояния
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладка приложения требует реализации таких функций управления выполнением, как шаг с заходом в функции, остановка в точках останова и продолжение выполнения. Visual Studio Debugging управляет выполнением событий, передаваемых между компонентами отладчика.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Элемент управления программой](../../extensibility/debugger/program-control.md)  
 Список следующих подпрограмм, происходящих на уровне программы: Установка следующего оператора, выполнение, выполнение шагов, продолжение, приостановка и возобновление.  
  
 [Методы, связанные с точкой останова](../../extensibility/debugger/breakpoint-related-methods.md)  
 Определяет связанные и ожидающие типы точек останова, которые поддерживает Visual Studio.  
  
 [Анализ стека вызова](../../extensibility/debugger/call-stack-evaluation.md)  
 Обсуждается реализация методов, позволяющих просматривать кадры стека стека вызовов в режиме приостановки выполнения.  
  
 [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Описывает, как подсистема отладки (DE), вычисление выражений (EE) и диспетчер отладки сеансов участвуют в анализе и вычислении выражения, указанного в одной из окон интегрированной среды разработки.  
  
 [События элементов управления](../../extensibility/debugger/control-events.md)  
 Описывает интерфейс, используемый для отправки событий во время управляемого выполнения программы.
