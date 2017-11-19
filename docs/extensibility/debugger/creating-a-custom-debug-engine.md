---
title: "Создание пользовательской модулю отладки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb5971bf86c6b97d38daaf86f3a093da196020da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-custom-debug-engine"></a>Создание модулем отладки
Отладчик (DE) — это компонент, позволяет выполнить отладку конкретного архитектур во время выполнения. Обычно имеется только одна реализация DE в среде выполнения.  
  
> [!NOTE]
>  Хотя отдельные реализации DE Transact-SQL и JScript, VBScript и JScript совместно использовать один DE.  
  
 DE работает с системой интерпретатор или операции для предоставления такие операции отладки, как выполнение элемента управления, точки останова и оценки выражений. Эти службы реализуются с помощью интерфейсов DE и может вызвать отладчик для перехода между различными режимами рабочей. Дополнительные сведения см. в разделе [рабочих режимов](../../extensibility/debugger/operational-modes.md).  
  
 Создание DE состоит из следующих шагов:  
  
1.  Регистрация DE в Visual Studio  
  
2.  Включение программы для отладки  
  
3.  Выполнение элемента управления и состояние оценки  
  
4.  Отправка событий  
  
5.  Завершение и отсоединение  
  
## <a name="in-this-section"></a>Содержание  
 [Регистрация пользовательского модуля отладки](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Описаны шаги, необходимые для регистрации модуля отладки в Visual Studio, чтобы он может использоваться.  
  
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Объясняет, что перед вашей DE можно отлаживать программы, сначала необходимо запустить DE или присоединить ее к существующей программы.  
  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Описывает, почему для отладки приложения требуется реализации выполнения функций управления.  
  
 [Отправка событий](../../extensibility/debugger/sending-events.md)  
 Описывает взаимодействие между отладчиком и DE как модель событий, в зависимости от DCOM.  
  
 [Завершение и отсоединение](../../extensibility/debugger/termination-and-detaching.md)  
 Описание способов достижения нормального завершения, это означает, что отсутствуют точки останова, исключения, ошибки во время выполнения или бесконечные циклы в приложении для отладки.  
  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)  
 Документирует порядок вызова события, происходящие во время сеанса отладки.  
  
 [Практическое руководство. Отладка пользовательского модуля отладки](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Объясняется, как выполнить отладку пользовательского DE.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)