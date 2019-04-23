---
title: Практическое руководство. Вернуться к функции, вызвавшей MFC, при прерывании работы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a86efc2e181a7f692e84244eecb2355783b188bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039375"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Практическое руководство. Возврат к функции, вызвавшей MFC, при прерывании работы в MFC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 При использовании команды **Прервать** из меню **Отладка** для остановки выполнения программы и завершения в MFC и при наличии ошибок в коде, можно вызвать окно "Стек вызовов" для обратного перехода к функции. Дополнительные сведения см. в разделе [Как использовать окно "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md).  
  
 Иногда код может прерываться в генераторе сообщений. В таком случае в стеке вызовов нет пользовательского кода. Во избежание этой проблемы используются точки останова (с условиями и количеством обращений) вместо команды **Прервать**. Дополнительные сведения см. в разделе [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Переход к функции, из которой был вызван MFC  
  
- Используйте окно **Стек вызовов**.  
  
## <a name="see-also"></a>См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)
