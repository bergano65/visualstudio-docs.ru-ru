---
title: Как выполнять отладку рабочих процессов на основе ASP.NET (прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668660"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Как отлаживать рабочие процессы, основанные на ASP.NET (для прежних версий)
В этом разделе описывается отладка основанных на [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] приложений [!INCLUDE[wf](../includes/wf-md.md)], которые ориентируются на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий.

 Отладку рабочих процессов прежних версий, которые запущены в ASP.NET, или рабочих процессов более ранней версии, которые опубликованы как веб-службы, можно выполнить посредством присоединения к процессу, в котором размещается рабочий процесс.

### <a name="to-debug-an-aspnet-based-workflow"></a>Отладка рабочих процессов, основанных на ASP.NET

1. Включите отладку для приложения ASP.NET, задав **debug = true** в файле web.config.

2. Установите библиотеку рабочего процесса как автозагружаемый проект, установите в рабочем процессе точки останова.

3. Введите URL веб-страницы по умолчанию в свойствах проекта рабочего процесса параметр **отладки** " **запустить браузер с помощью текстового поля" внешний URL-адрес** ".

4. Выберите **присоединить к процессу** в меню **Отладка** .

5. Выберите процесс для присоединения из списка **Доступные процессы** .

     Присоединение к процессу w3wp.exe, webdev.webserver или aspnet_wp, в котором размещается рабочий процесс.

6. Нажмите кнопку **выбрать** рядом с текстовым полем **присоединить к** .

     Откроется диалоговое окно **Выбор типа кода** .

7. Выберите **Отладка этих типов кода** и выберите **Рабочий процесс**.

8. Нажмите кнопку **ОК**.

9. Нажмите кнопку **Присоединить**.

10. Откройте веб-страницу по умолчанию в браузере и запустите рабочий процесс.

## <a name="see-also"></a>См. также:
 [Вызов отладчика Visual Studio для Windows Workflow Foundation (устаревшая)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [как установить точки останова в рабочих процессах (устаревший)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Отладка устаревших рабочих процессов](../workflow-designer/debugging-legacy-workflows.md)