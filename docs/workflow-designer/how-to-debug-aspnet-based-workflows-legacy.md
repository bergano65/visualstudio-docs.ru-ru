---
title: 'Конструктор рабочих процессов - как: отладки рабочих процессов на основе ASP.NET (для прежних версий)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975876"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Как отлаживать рабочие процессы, основанные на ASP.NET (для прежних версий)

В этом разделе описывается отладка приложений ASP.NET на базе Windows Workflow Foundation (WF), ориентированных на платформы .NET Framework версии 3.5 или WinFX в конструкторе рабочих процессов прежних версий Windows.

Отладку рабочих процессов прежних версий, которые запущены в ASP.NET, или рабочих процессов более ранней версии, которые опубликованы как веб-службы, можно выполнить посредством присоединения к процессу, в котором размещается рабочий процесс.

## <a name="to-debug-an-aspnet-based-workflow"></a>Отладка рабочих процессов, основанных на ASP.NET

1.  Включение отладки для приложения ASP.NET, задав **debug = true** в файле web.config.

2.  Установите библиотеку рабочего процесса как автозагружаемый проект, установите в рабочем процессе точки останова.

3.  Введите URL-адрес веб-страницы по умолчанию в свойствах проекта рабочего процесса **отладки** параметр **запуск обозревателя с внешний URL-адрес** текстовое поле.

4.  Выберите **присоединиться к процессу** на **отладки** меню.

5.  Выберите процесс для присоединения из **доступные процессы** списка.

     Присоединение к процессу w3wp.exe, webdev.webserver или aspnet_wp, в котором размещается рабочий процесс.

6.  Нажмите кнопку **выберите** рядом с **присоединение к** текстовое поле.

     **Выбор типа кода** откроется диалоговое окно.

7.  Выберите **отладить код следующих типов** и выберите **рабочего процесса**.

8.  Нажмите кнопку **ОК**.

9. Нажмите кнопку **Присоединить**.

10. Откройте веб-страницу по умолчанию в браузере и запустите рабочий процесс.

## <a name="see-also"></a>См. также

- [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Как задать точки останова в рабочих процессах (для прежних версий)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)