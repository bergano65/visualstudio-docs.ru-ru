---
title: 'Как: отладки рабочих процессов на основе ASP.NET (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: ed3f4f23ff02291df33b2676bdb980de191b281b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Как отлаживать рабочие процессы, основанные на ASP.NET (для прежних версий)
В этом разделе описывается отладка [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-основе [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] приложения, предназначенные либо [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] в конструкторе рабочих процессов прежних версий Windows.

 Отладку рабочих процессов прежних версий, которые запущены в ASP.NET, или рабочих процессов более ранней версии, которые опубликованы как веб-службы, можно выполнить посредством присоединения к процессу, в котором размещается рабочий процесс.

### <a name="to-debug-an-aspnet-based-workflow"></a>Отладка рабочих процессов, основанных на ASP.NET

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