---
title: Attach to Running Processes with the Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03cd890802e5563ce2daeb78438c56f4452d74f0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299514"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Присоединение к выполняемым процессам с использованием отладчика Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладчик Visual Studio можно подключить к запущенному процессу на локальном или удаленном компьютере. After the process is running, click **Debug / Attach to Process** (or press **CTRL+ALT+P**) to open the **Attach to Process** dialog box.

You can use this capability to debug apps that are running on a local or remote computer, debug multiple processes simultaneously, or debug an application that was not created in Visual Studio. It is often useful when you want to debug an app, but (for whatever reason) you did not start the app from Visual Studio with the debugger attached. For example, if you are running the app without the debugger and hit an exception, you might then attach to the process running the app to begin debugging.

> [!TIP]
> Not sure whether you need to use **Attach to Process** for your debugging scenario? See [Common debugging scenarios](#BKMK_Scenarios). If you want to debug ASP.NET applications that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a> Attach to a running process on the local machine
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names).

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. В диалоговом окне **Присоединение к процессу** найдите программу, к которой требуется присоединиться, в списке **Доступные процессы** .

     To quickly select the process you want, type the first letter of the process name. If you don't know the process name, see [Common debugging scenarios](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Если процесс выполняется с другой учетной записью пользователя, установите флажок **Показать процессы всех пользователей** .

3. Убедитесь, что в окне **Присоединиться к** указан тип кода, который необходимо отладить. Параметр по умолчанию **Авто** пытается определить тип кода, который нужно отладить. Чтобы вручную задать тип кода, выполните следующие действия.

    1. В поле **Присоединиться к** щелкните **Выбрать**.

    2. В диалоговом окне **Выбор типа кода** нажмите кнопку **Выполнять отладку кода следующих типов** и выберите типы для отладки.

    3. Нажмите кнопку **ОК**.

4. Нажмите кнопку **Присоединить**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Присоединение к процессу на удаленном компьютере
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names). For more complete guidance for ASP.NET apps that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Для других приложений, возможно, имя процесса удастся найти в диспетчере задач.

 При использовании диалогового окна **Присоединение к процессу** можно выбрать другой компьютер, который настроен для удаленной отладки. For more information, see [Remote Debugging](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). После выбора удаленного компьютера можно просмотреть список доступных процессов, запущенных на этом компьютере, и подключиться к одному или нескольким процессам для отладки.

 **To select a remote computer:**

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. В диалоговом окне **Присоединение к процессу** выберите подходящий тип подключения в списке **Транспорт** . **По умолчанию** — правильный параметр в большинстве случаев.

   Параметр **Транспорт** хранится между сеансами отладки.

3. Воспользуйтесь списком **Квалификатор** для выбора имени удаленного компьютера одним из следующих способов:

   1. Введите имя в списке **Квалификатор** .

      > [!NOTE]
      > If, in later steps, you can't connect using the remote computer name, use the IP address. (The port number may appear automatically after selecting the process. You can also enter it manually. In the illustration below, 4020 is the default port for the remote debugger.)

   2. Щелкните стрелку раскрывающегося списка **Квалификатор** и выберите из раскрывающегося списка имя компьютера.

   3. Click the **Find** button next to the **Qualifier** list to open the **Select Remote Debugger Connection** dialog box. В диалоговом окне **Выбор подключения к удаленному отладчику** будут перечислены все устройства, присутствующие в локальной подсети, а также устройства, непосредственно подключенные к компьютеру с помощью кабеля Ethernet (если таковые имеются). Щелкните нужный компьютер или устройство, после чего щелкните **Выбрать**.

      Параметр **Квалификатор** хранится между сеансами отладки только в случае успешного подключения отладки с этим квалификатором.

4. Нажмите кнопку **Обновить**.

     Список **Доступные процессы** отображается автоматически при открытии диалогового окна **Процессы** . Процессы могут запускаться и останавливаться в фоновом режиме, пока диалоговое окно открыто. Однако содержимое окна не всегда отражает текущее состояние. Можно обновить список в любое время, щелкнув кнопку **Обновить**, чтобы просмотреть текущий список процессов.

5. В диалоговом окне **Присоединение к процессу** найдите программу, к которой требуется присоединиться, в списке **Доступные процессы** .

    Если процесс выполняется с другой учетной записью пользователя, установите флажок **Показать процессы всех пользователей** .

6. Нажмите кнопку **Присоединить**.

## <a name="additional-info"></a>Additional info

Во время отладки можно подключиться к нескольким программам, но в любой момент времени только одна из них активна в отладчике. Можно выбрать текущую программу в панели инструментов **Место отладки** или окне **Процессы** . Дополнительные сведения см. в разделе [Практическое руководство: Установка текущей программы](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Если попытаться подключиться к процессу, работающему под управлением ненадежной учетной записи, появится диалоговое окно подтверждения с предупреждением безопасности. Дополнительные сведения см. в разделе [предупреждение системы безопасности: Присоединение к процессу, принадлежит недоверенному пользователю может быть опасно. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

В некоторых случаях при отладке в сеансе удаленного рабочего стола (службы терминалов), список **Доступные процессы** не отображает все доступные процессы. При работе с Visual Studio в качестве пользователя с ограниченным доступом в списке **Доступные процессы** не будут отображаться процессы, запущенные в сеансе 0, который используется для служб и других серверных процессов, включая w3wp.exe. Можно устранить эту проблему, запустив [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] под учетной записью администратора или запустив [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с консоли сервера вместо сеанса служб терминалов. Если ни один из этих обходных путей использовать невозможно, третий вариант — присоединение к процессу путем запуска `vsjitdebugger.exe -p` *ProcessId* из командной строки Windows. Можно определить идентификатор процесса с помощью Tlist.exe. Чтобы получить файл tlist.exe, скачайте и установите средства отладки для Windows, которые доступны на  [странице файлов загрузки WDK и WinDbg](https://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a> Common debugging scenarios

To help you identify whether you need to use **Attach to process** and what process to attach to, a few common debugging scenarios are shown here (the list is not exhaustive). Where more instructions are available, we provide links.

For some app types (like Windows Store apps), you don't attach directly to a process name, but use the **Debug Installed App Package** menu option instead (see table).

> [!NOTE]
> For information about basic debugging in Visual Studio, see [Getting started with the debugger](../debugger/getting-started-with-the-debugger.md).

|Сценарий|Debug Method|Имя процесса|Notes and Links|
|-|-|-|-|
|Debug a managed or native app on the local machine|Use attach to process or [standard debugging](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|To quickly access the dialog box, use **CTRL+ALT+P** and then type the first letter of the process name.|
|Debug ASP.NET apps on the local machine after starting the app without the debugger|Use attach to process|iiexpress.exe|This may be helpful to make your app load faster, such as (for example) when profiling. |
|Remote debug ASP.NET 4 or 4.5 on an IIS server|Use remote tools and attach to process|w3wp.exe|See [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remote debug ASP.NET Core on an IIS server|Use remote tools and attach to process|dnx.exe|For app deployment, see [Publish to IIS](https://docs.asp.net/en/latest/publishing/iis.html). For debugging, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debug other supported app types on a server process|Use remote tools (if server is remote) and attach to process|iexplore.exe or other processes|If necessary, use Task Manager to help identify the process. See [Remote Debugging](../debugger/remote-debugging.md) and later sections in this topic|
|Remote debug a Windows desktop app|Remote Tools and F5|Н/Д| See [Remote Debugging](../debugger/remote-debugging.md)|
|Remote debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app|Отладка установленного пакета приложения|Н/Д|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|
|Debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app that you didn't start from Visual Studio|Отладка установленного пакета приложения|Н/Д|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|

> [!WARNING]
> Для присоединения к универсальному приложению Windows, которое написано на JavaScript, сначала необходимо включить отладку для приложения. См. раздел [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) в Центре разработчика Windows.

> [!NOTE]
> Чтобы отладчик мог присоединиться к коду на языке C++, код должен предоставлять `DebuggableAttribute`. Это можно добавить в код автоматически, путем связывания с параметром [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) компоновщика.

## <a name="what-debugger-features-can-i-use"></a>What debugger features can I use?

To use the full features of the Visual Studio debugger (like hitting breakpoints) when attaching to a process, the executable must exactly match your local source and symbols (that is, the debugger must be able to load the correct [symbol (.pbd) files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). By default, this requires a debug build.

For remote debugging scenarios, you must have the source code (or a copy of the source code) already open in Visual Studio. The compiled app binaries on the remote machine must come from the same build as on the local machine.

In some local debugging scenarios, you can debug in Visual Studio with no access to the source if the correct symbol files are present with the app (by default, this requires a debug build). For more info, see [Specify Symbol and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Устранение ошибок присоединения
 При присоединении отладчика к выполняющемуся процессу этот процесс может содержать один или несколько типов кода. Типы кода, к которым может присоединиться отладчик, отображаются и выбираются в диалоговом окне **Выбор типа кода** .

 Иногда отладчик может успешно присоединяться к одному типу кода, но не к другому. Такое может происходить при попытке присоединения к процессу, выполняющемуся на удаленном компьютере. На удаленном компьютере для одних типов кода могут иметься компоненты удаленной отладки, а для других — нет. Такое также может происходить при попытке присоединиться к двум или более процессам для прямой отладки базы данных. Отладка SQL поддерживает присоединение только к одному процессу.

 Если отладчик может присоединиться не ко всем типам кода, то будет отображено сообщение, идентифицирующее типы, к которым присоединиться не удалось.

 Если отладчик успешно подключается хотя бы к одному типу кода, то можно приступать к отладке процесса. Но отлаживать можно будет только те типы кода, к которым удалось подсоединиться. В приведенном выше сообщении указано, что не удалось присоединиться к типу кода скриптов. Поэтому проводить отладку кода скриптов в данном процессе не удастся. Код скриптов в этом процессе будет выполняться, но задавать в этом сценарии точки останова, просматривать данные и выполнять другие операции отладки не удастся.

 Если нужны более конкретные сведения о том, почему отладчику не удалось присоединиться к некоторому типу кода, можно попытаться повторно присоединиться только к этому типу кода.

 **To obtain specific information about why a code type failed to attach**

1. Отключитесь от процесса. В меню **Отладка** выберите команду **Отсоединить все**.

2. Вновь подключитесь к процессу, выбрав единственный тип кода.

   1. В диалоговом окне **Присоединение к процессу** выберите процесс в списке **Доступные процессы** .

   2. Нажмите кнопку **Выбрать**.

   3. В диалоговом окне **Выбор типа кода** выберите **Выполнять отладку кода следующих типов** и выберите тип кода, к которому не удалось присоединиться. Отмените выбор всех остальных типов кода.

   4. Нажмите кнопку **ОК**. Диалоговое окно **Выбор типа кода** будет закрыто.

   5. В диалоговом окне **Присоединение к процессу** нажмите **Присоединиться**.

      На этот раз присоединение не пройдет полностью, и будет выдано сообщение о конкретной ошибке.

## <a name="see-also"></a>См. также раздел
 [Debug Multiple Processes](../debugger/debug-multiple-processes.md) [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md) [Remote Debugging](../debugger/remote-debugging.md)
