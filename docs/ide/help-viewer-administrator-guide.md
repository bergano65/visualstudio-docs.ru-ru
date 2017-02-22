---
title: "Руководство администратора Help Viewer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Руководство администратора Help Viewer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Средство просмотра справки позволяет управлять локальными установленными копиями справки для сетевых сред с доступом к Интернету или без него.  Локальное содержимое справки настраивается для каждого компьютера.  По умолчанию пользователи должны иметь права администратора для обновления своей локальной установленной справки.  
  
 Если сетевая среда позволяет клиентам получить доступ в Интернет, средство просмотра справки позволяет выполнять скрипты командной строки, чтобы развертывать локальное содержимое справки из Интернета.  
  
 Если сетевая среда не позволяет клиентам получить доступ в Интернет, средство просмотра справки может развертывать локальное содержимое справки из интрасети или из сетевой папки с общим доступом.  Кроме того, можно отключить параметры справки интегрированной среды разработки Visual Studio, например справку в Интернете или автономную справку, установку содержимого при первом запуске интегрированной среды разработки, задав службу содержимого в интрасети и управляя содержимым с использованием переопределений ключей реестра.  
  
 Базовый синтаксис выглядит следующим образом:  
  
 \<*path to*\>\\HlpCtntmgr.exe \/operation \<*argument*\> \/catalogname \<*name*\> \/locale \<*locale*\> \/sourceuri \<*.msha path or URL*\>  
  
 Дополнительные сведения о синтаксисе командной строки HlpCtntMgr.exe см. в разделе [Аргументы командной строки для диспетчера содержимого справки](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Дополнительные сведения о создании содержимого, создании конечной точки службы интрасети и аналогичных типах действий см. в средстве просмотра справки SDK.  
  
## Развертывание локального содержимого справки из Интернета  
 Можно использовать службу пакетов содержимого MSDN для локального развертывания содержимого справки из Интернета на клиентских компьютерах.  Используется следующий синтаксис:  
  
 \\\<*путь к*\>\\v2.2\\HlpCtntmgr.exe \/operation \<*имя*\> \/catalogname \<*имя\_каталога*\> \/locale \<*языковой\_стандарт*\>  
  
 Дополнительные сведения о синтаксисе командной строки HlpCtntMgr.exe см. в разделе [Аргументы командной строки для диспетчера содержимого справки](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Требования:  
  
-   Клиентские компьютеры должны иметь доступ к Интернету.  
  
-   Пользователи должны обладать правами администратора, чтобы обновлять, добавлять или удалять локальное содержимое справки после того, как оно было установлено.  
  
 Предупреждения:  
  
-   Источником справки по умолчанию по\-прежнему будет Интернет.  
  
    > [!TIP]
    >  Можно изменить источник по умолчанию для справки, изменив ключ реестра HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\14.0\\help\\UseOnlineHelp.  Дополнительные сведения см. в разделе [Переопределение диспетчера содержимого справки](../ide/help-content-manager-overrides.md).  
  
-   Клиентам по\-прежнему будет предлагаться установить базовое содержимое справки при первом запуске Visual Studio.  Можно отключить этот запрос, изменив ключ реестра HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\VisualStudio\\14.0\\Help\\DisableFirstRunHelpSelection.  
  
### Пример  
 Следующий пример устанавливает содержимое для Visual Studio на английском языке на клиентский компьютер.  
  
##### Установка содержимого на английском языке из Интернета  
  
1.  Нажмите кнопку **Пуск**, затем выберите команду **Выполнить**.  
  
2.  Введите следующее:  
  
     C:\\Program Files \(x86\)\\Microsoft Help Viewer\\v2.2\\hlpctntmgr.exe \/operation install \/catalogname VisualStudio14 \/locale en\-us  
  
3.  Нажмите клавишу ВВОД.  
  
## Развертывание предустановленного локального содержимого справки на клиентских компьютерах  
 Можно установить набор содержимого из сети на один компьютер, а затем скопировать этот установленный набор содержимого на другие компьютеры.  
  
 Требования:  
  
-   Компьютер, где устанавливается набор содержимого, должен иметь доступ к Интернету.  
  
-   Пользователи должны обладать правами администратора, чтобы обновлять, добавлять или удалять локальное содержимое справки после того, как оно было установлено.  
  
    > [!TIP]
    >  Если пользователи не имеют права администратора, рекомендуется отключить вкладку "Управление содержимым" в средстве просмотра справки.  Дополнительные сведения см. в разделе [Переопределение диспетчера содержимого справки](../ide/help-content-manager-overrides.md).  
  
 Предупреждения:  
  
-   Если пользователи не имеют права администратора, рекомендуется отключить вкладку "Управление содержимым" в средстве просмотра справки.  Дополнительные сведения см. в разделе [Переопределение диспетчера содержимого справки](../ide/help-content-manager-overrides.md).  
  
-   Источником справки по умолчанию по\-прежнему будет Интернет.  
  
-   Клиентам по\-прежнему будет предлагаться установить базовое содержимое справки при первом запуске Visual Studio.  Дополнительные сведения см. в разделе [Переопределение диспетчера содержимого справки](../ide/help-content-manager-overrides.md).  
  
### Создание набора содержимого  
 Прежде чем можно будет создать базовый набор содержимого, необходимо сначала удалить все локальное содержимое Visual Studio на целевом компьютере.  
  
##### Удаление локальной справки  
  
1.  В средстве просмотра справки выберите вкладку **Управление содержимым**.  
  
2.  В разделе **Доступная документация** перейдите к набору документов по Visual Studio.  
  
3.  Нажмите кнопку **Удалить** рядом с каждым вложенным элементом.  
  
4.  Выберите **Запуск**, чтобы удалить  
  
5.  Перейдите в папку *n*:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12 и убедитесь, что папка содержит только файл catalogType.xml.  
  
 После удаления всего ранее установленного локального содержимого справки Visual Studio можно загрузить базовый набор содержимого.  
  
##### Загрузка содержимого  
  
1.  В средстве просмотра справки выберите вкладку **Управление содержимым**.  
  
2.  В разделе **Доступная документация** перейдите к наборам документации, которые требуется загрузить, и затем выберите **Добавить**.  
  
3.  Щелкните **Запуск**.  
  
 После этого потребуется упаковать содержимое, чтобы его можно было развертывать на клиентских компьютерах.  
  
##### Упаковка содержимого  
  
1.  Создайте папку, чтобы скопировать содержимое для дальнейшего развертывания.  
  
     Например, c:\\VS12Help.  
  
2.  Откройте cmd.exe с разрешениями администратора.  
  
3.  Перейдите к папке, созданной на шаге 1.  
  
4.  Введите следующее:  
  
     Xcopy %SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2 \<*foldername*\>\\ \/y \/e \/k \/o  
  
     Пример: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### Развертывание содержимого  
  
##### Развертывание содержимого  
  
1.  Создайте сетевую папку и скопируйте содержимое справки в это место.  
  
     Например, скопируйте содержимое из c:\\VS12Help в \\\\myserver\\VS12Help.  
  
2.  Создайте BAT\-файл, чтобы поместить в него скрипт развертывания для содержимого справки.  Поскольку у клиента может быть установлена блокировка чтения на какой\-либо из файлов, удаляемых в рамках принудительной установки, необходимо завершить работу клиента, прежде чем принудительно устанавливать обновления.  
  
     Например:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  Запустите BAT\-файл на локальных компьютерах, на которых требуется установить содержимое справки.  
  
## См. также  
 [Аргументы командной строки для диспетчера содержимого справки](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Переопределение диспетчера содержимого справки](../ide/help-content-manager-overrides.md)