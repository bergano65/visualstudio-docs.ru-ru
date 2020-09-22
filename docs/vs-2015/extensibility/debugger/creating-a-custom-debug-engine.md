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
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843165"
---
# <a name="creating-a-custom-debug-engine"></a>Создание пользовательского модуля отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Модуль отладки (DE) — это компонент, позволяющий выполнять отладку определенных архитектур времени выполнения. Как правило, для среды выполнения обычно используется только одна дереализация.  
  
> [!NOTE]
> Хотя существуют отдельные реализации DE для Transact-SQL и JScript, VBScript и JScript совместно используют один DE.  
  
 DE работает с интерпретатором или системой операций для предоставления таких служб отладки, как управление выполнением, точки останова и вычисление выражений. Эти службы реализуются через интерфейсы DE и могут привести к переходу отладчика между различными операционными режимами. Дополнительные сведения см. в разделе [Рабочие режимы](../../extensibility/debugger/operational-modes.md).  
  
 Создание DE состоит из следующих шагов:  
  
1. Регистрация DE в Visual Studio  
  
2. Включение отладки программы  
  
3. Контроль выполнения и оценка состояния  
  
4. Отправка событий  
  
5. Завершение и отсоединение  
  
## <a name="in-this-section"></a>в этом разделе  
 [Регистрация пользовательского модуля отладки](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Описание действий, необходимых для регистрации модуля отладки в Visual Studio, чтобы его можно было использовать.  
  
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 В этой статье объясняется, что перед началом отладки программы необходимо сначала запустить DE или присоединить ее к существующей программе.  
  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Описывает, почему Отладка приложения требует реализации функций управления выполнением.  
  
 [Отправка событий](../../extensibility/debugger/sending-events.md)  
 Описывает взаимодействие между отладчиком и DE в качестве модели событий на основе DCOM.  
  
 [Завершение и отсоединение](../../extensibility/debugger/termination-and-detaching.md)  
 Объясняет, как добиться нормального завершения, что означает отсутствие точек останова, исключений, ошибок времени выполнения или бесконечных циклов в приложении для отладки.  
  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)  
 Документирует порядок вызовов событий, происходящих в сеансе отладки.  
  
 [Практическое руководство. Отладка пользовательского модуля отладки](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Объясняется, как выполнить отладку пользовательского DE.  
  
## <a name="see-also"></a>См. также:  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
