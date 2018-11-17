---
title: Параметры для конфигурации отладки C++ проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 404bbc753b2729ad5ec7625fa01803b8a6bdf5c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800800"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Параметры проекта для конфигурации отладки C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно изменить параметры проекта для конфигурации отладки C или Visual C++ в **страницы свойств** диалоговое окно, как описано в [как: Настройка отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md). В следующих таблицах показано, где можно найти параметры, связанные с отладчиком в **страницы свойств** диалоговое окно.  
  
> [!WARNING]
>  Параметры отладки проекта в **свойства конфигурации/Отладка** различаются категории для приложений Windows Store и компоненты, которые создаются на языке C++. См. в разделе [начать сеанс отладки (VB, C#, C++ и XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) в центре разработчиков Windows.  
  
 Укажите используемый отладчик в **отладчик для запуска** поле со списком. В зависимости от выбора, будут отображены те или иные свойства.  
  
 При сохранении решения каждый параметр свойств, связанных с отладкой, автоматически записывается и сохраняется в индивидуальном пользовательском файле (.vcxproj.user) для данного решения.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Папка "Свойства конфигурации" (категория "Отладка")  
  
|**Параметр**|**Описание**|  
|-----------------|---------------------|  
|**Отладчик для запуска**|Позволяет выбрать отладчик для запуска из следующих вариантов:<br /><br /> -   **Отладчик локального Windows**<br />-   **Windows удаленного отладчика**<br />-   **Отладчик веб-браузера**<br />-   **Отладчик веб-служб**|  
|**Команда** (отладчик локального Windows)|Задает команду для запуска отлаживаемой программы на локальном компьютере.|  
|**Удаленная команда** (Windows, удаленный отладчик)|Путь к EXE-файлу на удаленном компьютере. Путь следует вводить в том же виде, в каком он вводился бы на удаленном компьютере.|  
|**Аргументы команды** (отладчик локального Windows и Windows, удаленный отладчик)|— Указывает аргументы для указанной выше команды.<br /><br /> В этом поле можно использовать следующие операторы перенаправления:<br /><br /> < `file`<br /> Чтение потока stdin из файла.<br /><br /> > `file`<br /> Запись потока stdout в файл.<br /><br /> >> `file`<br /> Добавление потока stdout в файл.<br /><br /> 2> `file`<br /> Запись потока stderr в файл.<br /><br /> 2>> `file`<br /> Добавление потока stderr в файл.<br /><br /> 2> &1<br /> Перенаправление вывода потока stderr (2) в то же место назначения, что и у потока stdout (1).<br /><br /> 1> &2<br /> Перенаправление вывода потока stdout (1) в то же место назначения, что и у потока stderr (2).<br /><br /> В большинстве случаев эти операторы применимы только для консольных приложений.|  
|**Рабочий каталог**|Указывает рабочий каталог отлаживаемой программы относительно каталога проекта, в котором расположен исполняемый EXE-файл. Если оставить это поле пустым, каталогом проекта будет являться рабочий каталог. При удаленной отладке каталог проекта располагается на удаленном сервере.|  
|**Присоединение** (отладчик локального Windows и Windows, удаленный отладчик)|Указывает, запускать ли приложение или выполнять присоединение к этому приложению. По умолчанию выбрано значение "Нет".|  
|**Имя удаленного сервера** (Windows, удаленный отладчик)|Задает имя компьютера (не вашего), на котором предполагается производить отладку приложения.<br /><br /> Макрос сборки "RemoteMachine" принимает равно значению этого свойства. Дополнительные сведения см. в разделе [макросы для команд и свойств построения](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Подключение** (Windows, удаленный отладчик)|Выбор типа подключения для удаленной отладки: стандартное подключение или подключение без аутентификации. Укажите имя удаленного компьютера в **имя удаленного сервера** поле. Доступны следующие типы подключения:<br /><br /> -   **Удаленный доступ с аутентификацией Windows**<br />-   **Удаленный доступ без проверки подлинности (только машинный код)**<br /><br /> **Примечание** удаленной отладке без аутентификации может стать уязвимым удаленного компьютера с точки зрения безопасности. Режим аутентификации Windows является более безопасным.<br /><br /> Дополнительные сведения см. в разделе [Настройка удаленной отладки](../debugger/remote-debugging.md).|  
|**URL-адрес HTTP** (веб-служба отладчика и отладчик веб-браузера)|Указывает URL-адрес, по которому расположен отлаживаемый проект.|  
|**Тип отладчика**|Указывает тип отладчика: **только машинный код**, **только управляемый код**, **только графический Процессор**, **Mixed**, **автоматически**(по умолчанию), или **скрипт**.<br /><br /> -   **Только машинный код** для неуправляемого кода C++.<br />-   **Только управляемый код** для кода, выполняемого в общеязыковой среде выполнения (управляемый код).<br />-   **Смешанный** вызывает отладчики как для управляемого и неуправляемого кода.<br />-   **Автоматическое** определяет тип отладчика, на основе компилятора и сведения exe-файла.<br />-   **Сценарий** вызывает отладчик для скриптов.<br />-   **Только GPU** для кода C++ AMP, который выполняется на устройстве GPU или на средство программной прорисовки DirectX. См. в разделе [отладка кода GPU](../debugger/debugging-gpu-code.md).|  
|**Среда** (отладчик локального Windows)|Указывает переменные среды для отлаживаемой программы. Используйте стандартный синтаксис переменной среды (например, `PATH="%SystemRoot%\..."`). Эти переменные переопределяют системную среду или объединяются с системной средой, в зависимости от **Объединение среды** параметр. Если щелкнуть по столбцу параметров, появится элемент "Изменить...". Щелкните эту ссылку, чтобы изменить переменные среды.|  
|**Объединение среды** (отладчик локального Windows)|Определяет, являются ли переменные, указанные в **среды** поле будут объединены со средой, определяется операционной системой. По умолчанию выбрано значение "Да".|  
|**Отладка SQL** (все, кроме отладчика MPI-кластера)|Включает отладку SQL-процедур из приложения [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. По умолчанию выбрано значение "Нет".|  
|**Тип ускорителя отладки** (только для отладки GPU)|Указывает устройство GPU для отладки. При установке драйверов устройств для совместимых устройств GPU добавляются дополнительные параметры. По умолчанию установлено значение "Программный эмулятор GPU".|  
|**Стандартное поведение точек останова для GPU** (только для отладки GPU)|Указывает, должно ли событие точки останова вызываться для каждого потока в варпе SIMD. По умолчанию выбран однократный вызов события точки останова для каждого варпа.|  
|**Ускоритель по умолчанию для amp** (только для отладки GPU)|Определяет ускоритель, по умолчанию используемый для AMP при отладке кода GPU. Выберите **ускоритель по WARP** для расследования, если проблема вызвана оборудованием или драйвером, а не код.|  
|**Каталог развертывания** (Windows, удаленный отладчик)|Задает путь на удаленном компьютере, куда будут копироваться выходные данные проекта перед запуском. Путь может быть сетевой папкой на удаленном компьютере, либо это может быть путь к папке на удаленном компьютере. По умолчанию это поле пусто, что означает, что выходные данные проекта не копируются в сетевую папку. Чтобы включить развертывание файлов, необходимо также выбрать **развернуть** "флажок" в диалоговом окне Configuration Manager. Дополнительные сведения см. в разделе [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).|  
|**Дополнительные файлы для развертывания** (Windows, удаленный отладчик)|Если в поле "Каталог развертывания" задан каталог развертывания, в этом поле указывается список дополнительных файлов (разделяемых точкой с запятой), которые должны копироваться в каталог развертывания. По умолчанию это поле пусто, что означает, что никакие дополнительные файлы в каталог развертывания не копируются. Чтобы включить развертывание файлов, необходимо также выбрать **развернуть** "флажок" в диалоговом окне Configuration Manager. Дополнительные сведения см. в разделе [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).|  
|**Развертывание отладочных библиотек Visual C++ среды выполнения** (Windows, удаленный отладчик)|Если в поле "Каталог развертывания" задан каталог развертывания, данный параметр указывает, должны ли библиотеки времени выполнения отладки Visual C++ для текущей платформы копироваться в сетевую папку. Значением по умолчанию является "Да".|  
  
### <a name="cc-folder-general-category"></a>Папка "C/C++" (категория "Общие")  
  
|Параметр|Описание:|  
|-------------|-----------------|  
|**Формат отладочной информации** ([/Z7, / Zd, Zi, /ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Указывает тип отладочных данных, создаваемых для проекта.<br /><br /> По умолчанию установлен формат /ZI, означающий создание базы данных программы (PDB) в формате, совместимом с операцией "Изменить и продолжить". Дополнительные сведения см. в разделе [/Z7, / Zd, / Zi, /ZI (формат отладочной информации)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Папка "C/C++" (категория "Оптимизация")  
  
|Параметр|Описание:|  
|-------------|-----------------|  
|**Optimization**|Указывает, должен ли компилятор оптимизировать создаваемый им код. При оптимизации исполняемый код изменяется. Оптимизированный код не совпадает в точности с исходным кодом. Это усложняет отладку.<br /><br /> Параметр по умолчанию (**отключено (/ 0d**) отключает оптимизацию. Можно производить разработку при отключенной оптимизации и включить оптимизацию только при создании рабочей версии программы.|  
  
### <a name="linker-folder-debugging-category"></a>Папка "Компоновщик" (категория "Отладка")  
  
|Параметр|Описание:|  
|-------------|-----------------|  
|**Создавать отладочную информацию** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Указывает компоновщику необходимость включать сведения, формат которых задается ключом /Z7, /Zd, Zi или /ZI.|  
|**Создавать файл базы данных программы** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|В этом поле вводится имя PDB-файла. Должен быть выбран формат отладочной информации ZI или /Zi.|  
|**Удалить закрытые символы** ([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|В этом поле задается имя PDB-файла в том случае, если в PDB-файл не должны выводиться закрытые символы. Этот параметр создает второй файл базы данных программы (PDB) при сборке образа программы с любыми параметрами компилятора или компоновщика, при которых создается PDB-файл (такими как /DEBUG, /Z7, /Zd или /Zi). Второй PDB-файл не содержит символов, которые нежелательно передавать клиентам. Дополнительные сведения см. в разделе [Параметр /PDBSTRIPPED (пропуск частных символов)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Создавать файл сопоставления** ([/MAP](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Указывает компоновщику на необходимость создания файла сопоставления во время компоновки. По умолчанию выбрано значение "Нет". Дополнительные сведения см. в разделе [Параметр /MAP (создание файла сопоставления)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Имя файла сопоставления** ([/MAP:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*имя*)|Если выбрано создание файла сопоставления, в этом поле можно указать имя файла сопоставления. Дополнительные сведения см. в разделе [Параметр /MAP (создание файла сопоставления)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Сопоставлять экспортируемые функции** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Включение экспортируемых функций в файл сопоставления. По умолчанию выбрано значение "Нет". Дополнительные сведения см. в разделе [/MAPINFO (Включение сведений в файл сопоставления)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Отлаживаемая сборка** ([/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Задает параметры для параметра компоновщика /ASSEMBLYDEBUG. Ниже приведены возможные значения.<br /><br /> -   **Атрибут debuggable не порождается**.<br />-   **Среда выполнения отслеживания и отключение оптимизации (/ ASSEMBLYDEBUG)**. Это значение установлено по умолчанию.<br />-   **Нет среды выполнения отслеживания и включите optimizations(/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<наследовать от родителя или проекта значения по умолчанию >**.<br />— Дополнительные сведения см. в разделе [/ASSEMBLYDEBUG (Добавление атрибута DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Эти параметры в папке "Свойства конфигурации" (категория "Отладка") можно изменить программным путем с помощью интерфейса Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Создание проектов Visual C++ и управление ими](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ ASSEMBLYDEBUG (Добавление атрибута DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Стандартные макросы для команд и свойств сборки](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



