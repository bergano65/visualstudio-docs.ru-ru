---
title: Remote Debugging | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300552"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете отладить приложение Visual Studio, развернутое на другом компьютере.  Для этого используется удаленный отладчик Visual Studio.  
  
 Информация в этом разделе относится к классическим приложениям Windows и приложениям ASP.NET.  For information about remote debugging Windows Store apps and Azure apps, see [Remote Debugging on Windows Store and Azure apps](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Get the remote tools  
You can either download the remote tools directly on the device or server that you want to debug, or you can get the remote tools from your host machine with Visual Studio installed.

### <a name="to-download-and-install-the-remote-tools"></a>To download and install the remote tools
  
1. On the device or server machine that you want to debug (rather than the machine running Visual Studio), get the correct version of the remote tools.

    |Version|Ссылка|Примечания|
    |-|-|-|
    |Visual Studio 2015 с обновлением 3|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary. Always download the version matching your device operating system (x86, x64, or  ARM version)|
    |Visual Studio 2015 (older)|[Инструменты удаленной отладки](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary.|
    |Visual Studio 2013|[Инструменты удаленной отладки](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2013 documentation|
    |Visual Studio 2012|[Инструменты удаленной отладки](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2012 documentation|
  
2. On the download page, choose the version of the tools that matches your operating system (x86, x64, or  ARM version) and download the remote tools.
  
    > [!IMPORTANT]
    > We recommend you install the most recent version of the remote tools that matches your version of Visual Studio. Mismatched versions are not recommended.  
    >   
    >  In addition, you must install the remote tools that have the same architecture as the operating system on which you want to install it. In other words, if you want to debug a 32-bit application on a remote computer running a 64-bit operating system, you must install the 64-bit version of the remote tools on the remote computer.  
  
3. Скачав исполняемый файл, следуйте инструкциям по установке приложения на удаленном компьютере. See [setup instructions](#bkmk_setup)

If you try to copy the remote debugger (msvsmon.exe) to the remote computer and run it, be aware that the **Remote Debugger Configuration Wizard** (**rdbgwiz.exe**) is installed only when you download the tools, and you may need to use the wizard for configuration later, especially if you want the remote debugger to run as a service. For more information, see [(Optional) Configure the remote debugger as a service](#bkmk_configureService) below.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>To run the remote debugger from a file share

You can find the remote debugger (**msvsmon.exe**) on a computer with Visual Studio 2015 Community, Professional, or Enterprise already installed. For many scenarios, the easiest way to set up remote debugging is to run the remote debugger (msvsmon.exe) from a file share. For usage limitations, see the remote debugger's Help page (**Help / Usage** in the remote debugger).

1. Find **msvsmon.exe** in the directory matching your version of Visual Studio. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Share the **Remote Debugger** folder on the Visual Studio computer.

3. On the remote computer, run **msvsmon.exe**. Follow the [setup instructions](#bkmk_setup).

> [!TIP] 
> For command line installation and command line reference, see the Help page for **msvsmon.exe** by typing ``msvsmon.exe /?`` in the command line on the computer with Visual Studio installed (or go to **Help / Usage** in the remote debugger).

## <a name="supported-operating-systems"></a>Supported Operating Systems  
 Удаленный компьютер должен работать под управлением одной из следующих операционных систем:  
  
- Windows 10  
  
- Windows 8 или 8.1  
  
- Windows 7 с пакетом обновления 1 (SP1)  
  
- Windows Server 2012 или Windows Server 2012 R2  
  
- Windows Server 2008 с пакетом обновления 2 (SP2), Windows Server 2008 R2 с пакетом обновления 1 (SP1)  
  
## <a name="supported-hardware-configurations"></a>Поддерживаемые конфигурации оборудования  
  
- Процессор с тактовой частотой 1,6 ГГц или большей  
  
- 1 ГБ ОЗУ (1,5 ГБ при выполнении в виртуальной машине)  
  
- 1 ГБ свободного дискового пространства  
  
- Жесткий диск 5400 об/мин  
  
- Видеоадаптер с поддержкой DirectX 9 и разрешением экрана 1024x768 или выше  
  
## <a name="network-configuration"></a>Сетевая конфигурация  
 Удаленный компьютер и компьютер Visual Studio должны быть подключены по сети, объединены в рабочую или домашнюю группу либо соединены напрямую с помощью кабеля Ethernet. Отладка через Интернет не поддерживается.  
  
## <a name="bkmk_setup"></a>Set up the remote debugger  
 на удаленном компьютере требуются права администратора.  
  
1. Найдите приложение "Удаленный отладчик". (Open the Start menu and search for **Remote Debugger**.)
  
    If you are running the remote debugger on a  remote server, you can right-click the Remote Debugger app and choose **Run as administrator** (Or, you can run the remote debugger as a service).If you are not running it on a remote server, just start it normally.
  
2. When you start the remote tools for the first time (or before you have configured it), the **Remote Debugging Configuration** dalog box appears.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. If the Windows Service API is not installed (which happens only on Windows Server 2008 R2), choose the **Install** button.  
  
4. Выберите типы сетей, в которых необходимо использовать инструменты удаленной отладки. Должен быть выбран по крайней мере один тип сети. Если компьютеры соединены через домен, необходимо выбрать первый пункт. Если компьютеры соединены посредством рабочей или домашней группы, необходимо выбрать второй или третий пункт.  
  
5. Choose **Configure remote debugging** to configure the firewall and start the tool.  
  
6. По завершении настройки появится окно удаленного отладчика.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    The remote debugger is now waiting for a connection. Make a note of the server name and port number that is displayed, because you will need this later for configuration in Visual Studio.  
  
   When you are finished debugging and need to stop the remote debugger, click **File / Exit** on the window. You can restart it from the **Start** menu or from the command line:  
  
   **\<Visual Studio installation directory>\Common7\IDE\Remote Debugger\\<x86, x64, or Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Настройка удаленного отладчика  
 После первого запуска удаленного отладчика можно изменить некоторые аспекты его конфигурации.
  
- To enable other users to connect to the remote debugger, choose **Tools / Permissions**. Для предоставления разрешений или отказа в предоставлении необходимо обладать правами администратора.

  > [!IMPORTANT]
  > You can run the remote debugger under a user account that differs from the user account you are using on the Visual Studio computer, but you must add the different user account to the remote debugger's permissions. 

   Alternatively, you can start the remote debugger from the command line with the **/allow \<username>** parameter: **msvsmon /allow \<username@computer** .
  
- To change the Authentication mode or the port number, or to specify a timeout value for the remote tools: choose **Tools / Options**.  
  
   For a listing of the port numbers used by default, see [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Вы можете запускать инструменты удаленной отладки в режиме "без аутентификации", однако настоятельно рекомендуется не использовать этот режим. При работе в этом режиме сетевая безопасность не обеспечивается. Режим без аутентификации можно выбрать, только если вы уверены в отсутствии вредоносного или опасного трафика.

## <a name="bkmk_configureService"></a> (Optional) Configure the remote debugger as a service
 For debugging in ASP.NET and other server environments, you must either run the remote debugger as an Administrator or, if you want it always running,  run the remote debugger as a service.
  
 If you want to configure the remote debugger as a service, follow these steps.  
  
1. Найдите **мастер настройки удаленного отладчика** (rdbgwiz.exe). (This is a separate application from the Remote Debugger.) It is available only when you install the remote tools. Вместе с Visual Studio он не устанавливается.  
  
2. Запустите мастер настройки. Когда появится первая страница, нажмите кнопку **Далее**.  
  
3. Установите флажок **Запускать удаленный отладчик Visual Studio 2015 как службу** .  
  
4. Добавьте имя учетной записи пользователя и пароль.  
  
    Для этой учетной записи может потребоваться добавить разрешение **Вход в качестве службы** . (Найдите элемент **Локальная политика безопасности** (secpol.msc) на **начальной** странице или в начальном окне (либо введите **secpol** в командной строке). В открывшемся окне дважды щелкните элемент **Назначение прав пользователя**, а затем в области справа найдите элемент **Вход в качестве службы** . Дважды щелкните его. Add the user account to the **Properties** window and click **OK**.) Click **Next**.  
  
5. Выберите тип сети, с которой должны взаимодействовать инструменты удаленной отладки. Должен быть выбран по крайней мере один тип сети. Если компьютеры соединены через домен, необходимо выбрать первый пункт. Если компьютеры соединены посредством рабочей или домашней группы, необходимо выбрать второй или третий пункт. Нажмите кнопку **Далее**.  
  
6. Если службу удается запустить, вы увидите сообщение **Вы успешно завершили работу мастера настройки удаленного отладчика Visual Studio**. Если службу не удается запустить, вы увидите сообщение **Не удалось завершить мастер настройки удаленного отладчика Visual Studio**. На странице также приводится ряд советов по запуску службы.  
  
7. Нажмите кнопку **Готово**.  
  
   Теперь удаленный отладчик должен работать как служба. Чтобы проверить, так ли это, выберите **Панель управления/Службы** и найдите службу **Удаленный отладчик Visual Studio 2015**.  
  
   Останавливать и запускать службу удаленного отладчика можно с помощью компонента **Панель управления / Службы**.  

## <a name="remote-debug-an-aspnet-application"></a>Удаленная отладка приложения ASP.NET  
 Развертывание приложения ASP.NET на удаленном компьютере со службами IIS выполняется по-разному в зависимости от операционной системы и версии IIS. For remote computers running Windows Server 2008 or Windows Server 2012 that have IIS 7.5 or later installed, please see [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 If you are debugging an ASP.NET Core app, please see [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html). Different steps are required to publish an ASP.NET Core on IIS. Once you publish an ASP.NET Core app successfully, you can remote debug it [just like other ASP.NET apps](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), except that the process you need to attach to is dnx.exe instead of w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Удаленная отладка проекта Visual C++  
 In the following procedure, the name and path of the project is C:\remotetemp\MyMfc, and the name of the remote computer is **MJO-DL**.  
  
1. Создайте приложение MFC с именем **mymfc**.  
  
2. Создайте точку останова в легкодоступном месте приложения, например в файле **MainFrm.cpp**, в начале `CMainFrame::OnCreate`.  
  
3. In Solution Explorer, right-click on the project and select **Properties**. Откройте вкладку **Отладка**.  
  
4. Для параметра **Загружаемый отладчик** задайте значение **Удаленный отладчик Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Внесите в свойства следующие изменения:  
  
   |Параметр|значения|
   |-|-|  
   |Удаленная команда|C:\remotetemp\mymfc.exe|  
   |Рабочий каталог|C:\remotetemp|  
   |Имя удаленного сервера|MJO-DL:*portnumber*|  
   |Подключение|Удаленный доступ с аутентификацией Windows|  
   |Тип отладчика|Только машинный код|  
   |Каталог развертывания|C:\remotetemp.|  
   |Дополнительные файлы развертывания|C:\data\mymfcdata.txt.|  
  
    If you deploy additional files (optional), the folder must exist on both machines.  
  
6. In Solution Explorer, right-click the solution and choose **Configuration Manager**.  
  
7. Для конфигурации **Отладка** установите флажок **Развертывание**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Start debugging (**Debug / Start Debugging**, or **F5**).  
  
9. Исполняемый файл автоматически развернется на удаленном компьютере.  
  
10. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials are specific to your network's security configuration. For example, on a domain computer, you might choose a security certificate or enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.  
  
11. На компьютере с Visual Studio вы должны увидеть, что выполнение остановилось в точке останова.  
  
    > [!TIP]
    > Кроме того, файлы можно развернуть как отдельный шаг. В **обозревателе решений** щелкните правой кнопкой мыши узел **mymfc** и выберите пункт **Развернуть**.  
  
    Если приложение должно использовать файлы, не являющиеся файлами кода, их нужно включить в проект Visual Studio. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). На странице **Свойства** для каждого файла задайте для свойства **Копировать в выходной каталог** значение **Всегда копировать**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Удаленная отладка проекта Visual C# или Visual Basic  
 Отладчик не может развертывать классические приложения Visual C# и Visual Basic на удаленном компьютере, но вы все же можете выполнять их удаленную отладку описанным ниже образом. The following procedure assumes that you want to debug it on a computer named **MJO-DL**, as shown in the earlier illustration.
  
1. Создайте проект WPF с именем **MyWpf**.  
  
2. Установите точку останова в легкодоступном месте кода.  
  
    Например, ее можно установить в обработчике кнопки. To do this, open MainWindow.xaml, and add a Button control from the Toolbox, then double-click the button to open it's handler.
  
3. В обозревателе решений щелкните правой кнопкой мыши проект и выберите пункт **Свойства**.  
  
4. На странице **Свойства** откройте вкладку **Отладка**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Убедитесь, что текстовое поле **Рабочий каталог** пустое.  
  
6. Choose **Use remote machine**, and type **MJO-DL:4020** in the text box. (4020 is the port number shown in the remote debugger window).  
  
7. Убедитесь в том, что параметр **Разрешить отладку машинного кода** не выбран.  
  
8. Выполните построение проекта.  
  
9. Создайте на удаленном компьютере папку с тем же путем, что и у папки **Debug** на компьютере с Visual Studio: **\<исходный путь>\MyWPF\MyWPF\bin\Debug**.  
  
10. Скопируйте исполняемый файл, сборку которого вы только что выполнили, с компьютера с Visual Studio в созданную на удаленном компьютере папку.
  
    > [!CAUTION]
    > Do not make changes to the code or rebuild (or you must repeat this step). Исполняемый файл, скопированный на удаленный компьютер, должен в точности совпадать с локальным исходным кодом и символами.

    You can copy the project manually, use Xcopy, Robocopy, Powershell, or other options.
  
11. Make sure the remote debugger is running on the target machine. (If it's not, search for **Remote Debugger** in the **Start** menu. ) The remote debugger window looks like this.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio, start debugging (**Debug / Start Debugging**, or **F5**).  
  
13. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials vary depending on your network's security configuration. For example, on a domain computer, you can  enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.

     Главное окно приложения WPF должно быть открыто на удаленном компьютере.
  
14. If necessary, take action to hit the breakpoint. Она должна быть активна. Если она не активна, символы для приложения не загрузились. Retry, and if that doesn't work, get information about loading symbols and how troubleshoot them at [Understanding symbol files and Visual Studio’s symbol settings](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. На компьютере с Visual Studio вы должны увидеть, что выполнение остановилось в точке останова.
  
    Если приложение должно использовать файлы, не являющиеся файлами кода, их нужно включить в проект Visual Studio. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). На странице **Свойства** для каждого файла задайте для свойства **Копировать в выходной каталог** значение **Всегда копировать**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Настройка отладки с удаленными символами  
 Вы можете отлаживать код с использованием символов, созданных на компьютере Visual Studio. Производительность удаленного отладчика гораздо выше при использовании локальных символов.  Если необходимо использовать удаленные символы, укажите, что монитор удаленной отладки должен искать символы на удаленном компьютере.  
  
 Начиная с версии Visual Studio 2013 с обновлением 2 можно использовать следующий параметр командной строки msvsmon для использования удаленных символов для управляемого кода: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 For more information, please see the remote debugging help (press **F1** in the remote debugger window, or click **Help / Usage**). Также см. запись блога с описанием [изменений, связанных с удаленной загрузкой символов .NET в Visual Studio 2012 и 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).  
  
## <a name="bkmk_winstoreAzure"></a> Remote Debugging on Windows Store and Azure apps  
 For information about remote debugging with Windows Store apps, see [Debug and test Windows Store apps on a remote device from Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Сведения об отладке в Azure см. в одном из следующих разделов:  
  
- [Debugging a Cloud Service or Virtual Machine in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debugging the .NET Backend in Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introduction to Remote Debugging on Azure Web Sites ([Part 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Part 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Part 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Удаленная отладка ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)
