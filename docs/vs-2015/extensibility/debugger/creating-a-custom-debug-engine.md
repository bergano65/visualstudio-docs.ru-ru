---
title: Создание пользовательского модуля отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a0617d23b49af182504406417023b0d907cadf27
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979607"
---
# <a name="creating-a-custom-debug-engine"></a>Создание пользовательского модуля отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладчик (DE) — это компонент, позволяет выполнить отладку конкретного архитектур во время выполнения. Обычно имеется только одна реализация DE каждой среды выполнения.  
  
> [!NOTE]
>  Несмотря на наличие отдельных реализаций DE Transact-SQL и JScript, VBScript и JScript совместно используют один DE.  
  
 DE работает с интерпретатором или операции система могла предоставлять такие операции отладки, как выполнение элемента управления, точки останова и оценки выражений. Эти службы реализуются с помощью интерфейсов DE и может вызвать отладчик для перехода между различные рабочие режимы. Дополнительные сведения см. в разделе [рабочие режимы](../../extensibility/debugger/operational-modes.md).  
  
 Создание DE состоит из следующих действий:  
  
1.  Регистрация Развернутой с помощью Visual Studio  
  
2.  Включение программы для отладки  
  
3.  Выполнение управления и состояние оценки  
  
4.  Отправка событий  
  
5.  Завершение и отсоединение  
  
## <a name="in-this-section"></a>В этом разделе  
 [Регистрация пользовательского модуля отладки](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Описание шагов, необходимых для регистрации модуля отладки в Visual Studio, чтобы можно было использовать.  
  
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Объясняет, что прежде чем ваши DE можно отлаживать программы, сначала необходимо запустить DE или присоединить ее к существующей программы.  
  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Описывает, почему для отладки приложения требуется реализации выполнения функций управления.  
  
 [Отправка событий](../../extensibility/debugger/sending-events.md)  
 Описывает взаимодействие между отладчиком и DE как модель событий, в зависимости от DCOM.  
  
 [Завершение и отсоединение](../../extensibility/debugger/termination-and-detaching.md)  
 Объясняется, как обеспечить нормальное завершение, это означает, что отсутствуют точки останова, исключения, ошибки времени выполнения или бесконечных циклов в приложении для отладки.  
  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)  
 Описывает порядок вызова событий, происходящих во время сеанса отладки.  
  
 [Практическое руководство. Отладка пользовательского модуля отладки](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 В этой статье описывается Отладка пользовательского DE.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
