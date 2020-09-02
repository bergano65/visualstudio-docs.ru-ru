---
title: Параметры проекта для конфигурации отладки C++ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ca9ff0678ba2c7abafa0d988efa09437ccd27dca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687558"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Параметры проекта для конфигурации отладки C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно изменить параметры проекта для конфигурации отладки C или Visual C++ в диалоговом окне **страницы свойств** , как описано в разделе [как задать конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md). В следующих таблицах показано, где в диалоговом окне **Страницы свойств** можно найти параметры, связанные с отладчиком.  
  
> [!WARNING]
> Параметры проекта отладки в категории **Свойства конфигурации/отладка** для приложений и компонентов магазина Windows, написанных на языке C++, отличаются. См. раздел [Запуск сеанса отладки (VB, C#, C++ и XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) в центре разработки Windows.  
  
 Укажите, какой отладчик использовать в списке **отладчик для запуска** . В зависимости от выбора, будут отображены те или иные свойства.  
  
 При сохранении решения каждый параметр свойств, связанных с отладкой, автоматически записывается и сохраняется в индивидуальном пользовательском файле (.vcxproj.user) для данного решения.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Папка "Свойства конфигурации" (категория "Отладка")  
  
|**Параметр**|**Описание**|  
|-----------------|---------------------|  
|**Отладчик для запуска**|Позволяет выбрать отладчик для запуска из следующих вариантов:<br /><br /> -   **Локальный отладчик Windows**<br />-   **Удаленный отладчик Windows**<br />-   **Отладчик веб-браузера**<br />-   **Отладчик веб-служб**|  
|**Команда** (локальный отладчик Windows)|Задает команду для запуска отлаживаемой программы на локальном компьютере.|  
|**Удаленная команда** (удаленный отладчик Windows)|Путь к EXE-файлу на удаленном компьютере. Путь следует вводить в том же виде, в каком он вводился бы на удаленном компьютере.|  
|**Аргументы команды** (локальный отладчик Windows и удаленный отладчик Windows)|— Задает аргументы для указанной выше команды.<br /><br /> В этом поле можно использовать следующие операторы перенаправления:<br /><br /> < `file`<br /> Чтение потока stdin из файла.<br /><br /> > `file`<br /> Запись потока stdout в файл.<br /><br /> >> `file`<br /> Добавление потока stdout в файл.<br /><br /> 2> `file`<br /> Запись потока stderr в файл.<br /><br /> 2>> `file`<br /> Добавление потока stderr в файл.<br /><br /> 2> &1<br /> Перенаправление вывода потока stderr (2) в то же место назначения, что и у потока stdout (1).<br /><br /> 1> &2<br /> Перенаправление вывода потока stdout (1) в то же место назначения, что и у потока stderr (2).<br /><br /> В большинстве случаев эти операторы применимы только для консольных приложений.|  
|**Рабочий каталог**|Указывает рабочий каталог отлаживаемой программы относительно каталога проекта, в котором расположен исполняемый EXE-файл. Если оставить это поле пустым, каталогом проекта будет являться рабочий каталог. При удаленной отладке каталог проекта располагается на удаленном сервере.|  
|**Присоединиться** (локальный отладчик Windows и удаленный отладчик Windows)|Указывает, запускать ли приложение или выполнять присоединение к этому приложению. По умолчанию выбрано значение "Нет".|  
|**Имя удаленного сервера** (удаленный отладчик Windows)|Задает имя компьютера (не вашего), на котором предполагается производить отладку приложения.<br /><br /> Для макроса сборки RemoteMachine задается значение этого свойства. Дополнительные сведения см. в разделе [макросы для команд и свойств сборки](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Подключение** (удаленный отладчик Windows)|Выбор типа подключения для удаленной отладки: стандартное подключение или подключение без аутентификации. Укажите имя удаленного компьютера в поле **Имя удаленного сервера**. Доступны следующие типы подключения:<br /><br /> -   **Удаленный доступ с проверкой подлинности Windows**<br />-   **Удаленно без проверки подлинности (только машинный код)**<br /><br /> **Примечание.** При удаленной отладке без проверки подлинности удаленный компьютер может стать уязвимым с точки зрения безопасности. Режим аутентификации Windows является более безопасным.<br /><br /> Дополнительные сведения см. в разделе [Установка удаленной отладки](../debugger/remote-debugging.md).|  
|**URL-адрес HTTP** (отладчик веб-служб и отладчик веб-браузера)|Указывает URL-адрес, по которому расположен отлаживаемый проект.|  
|**Тип отладчика**|Указывает тип используемого отладчика: **Только машинный код**, **Только управляемый код**, **Только GPU**, **Смешанный код**, **Авто** (по умолчанию) или **Скрипт**.<br /><br /> -   **Только машинный код** — используется для неуправляемого кода C++.<br />-   **Только управляемый код** — используется для кода, выполняемого в среде CLR (управляемого кода).<br />-   **Смешанный код** — вызывает отладчики как для управляемого, так и для неуправляемого типов кода.<br />-   **Авто** — определяет тип отладчика на основании информации компилятора и исполняемого файла.<br />-   **Скрипт** — вызывает отладчик для скриптов.<br />-   **Только графический процессор** — для кода C++ AMP, который выполняется на устройстве GPU или на средстве программной прорисовки DirectX. См. раздел [Отладка кода GPU](../debugger/debugging-gpu-code.md).|  
|**Окружение** (локальный отладчик Windows)|Указывает переменные среды для отлаживаемой программы. Используйте стандартный синтаксис для переменных среды (например, `PATH="%SystemRoot%\..."`). Эти переменные переопределяют системную среду или объединяются с ее переменными, в зависимости от значения параметра **Объединение среды**. Если щелкнуть по столбцу параметров, появится элемент "Изменить...". Щелкните эту ссылку, чтобы изменить переменные среды.|  
|**Объединение среды** (локальный отладчик Windows)|Определяет, будут ли переменные, указанные в поле **Среда**, объединяться со средой, определяемой операционной системой. По умолчанию выбрано значение "Да".|  
|**Отладка SQL** (все, за исключением отладчика MPI-кластера)|Включает отладку SQL-процедур из приложения [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. По умолчанию выбрано значение "Нет".|  
|**Тип ускорителя отладки** (только для отладки GPU)|Указывает устройство GPU для отладки. При установке драйверов устройств для совместимых устройств GPU добавляются дополнительные параметры. По умолчанию установлено значение "Программный эмулятор GPU".|  
|**Стандартное поведение точек останова для GPU** (только для отладки GPU)|Указывает, должно ли событие точки останова вызываться для каждого потока в варпе SIMD. По умолчанию выбран однократный вызов события точки останова для каждого варпа.|  
|**Ускоритель по умолчанию amp** (только для отладки GPU)|Определяет ускоритель, по умолчанию используемый для AMP при отладке кода GPU. Выберите **Ускоритель ПО WARP**, чтобы выяснить, вызвана ли проблема оборудованием или драйвером, а не кодом.|  
|**Каталог развертывания** (удаленный отладчик Windows)|Задает путь на удаленном компьютере, куда будут копироваться выходные данные проекта перед запуском. Путь может быть сетевой папкой на удаленном компьютере, либо это может быть путь к папке на удаленном компьютере. По умолчанию это поле пусто, что означает, что выходные данные проекта не копируются в сетевую папку. Чтобы включить развертывание файлов, нужно также установить флажок **Развертывание** в диалоговом окне "Диспетчер конфигураций". Дополнительные сведения см. [в разделе инструкции. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).|  
|**Дополнительные файлы развертывания** (удаленный отладчик Windows)|Если в поле "Каталог развертывания" задан каталог развертывания, в этом поле указывается список дополнительных файлов (разделяемых точкой с запятой), которые должны копироваться в каталог развертывания. По умолчанию это поле пусто, что означает, что никакие дополнительные файлы в каталог развертывания не копируются. Чтобы включить развертывание файлов, нужно также установить флажок **Развертывание** в диалоговом окне "Диспетчер конфигураций". Дополнительные сведения см. [в разделе инструкции. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).|  
|**Развертывание отладочных библиотек времени выполнения Visual C++** (удаленный отладчик Windows)|Если в поле "Каталог развертывания" задан каталог развертывания, данный параметр указывает, должны ли библиотеки времени выполнения отладки Visual C++ для текущей платформы копироваться в сетевую папку. Значением по умолчанию является "Да".|  
  
### <a name="cc-folder-general-category"></a>Папка "C/C++" (категория "Общие")  
  
|Параметр|Описание|  
|-------------|-----------------|  
|**Формат отладочной информации** ([/Z7, /Zd, Zi, /ZI](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Указывает тип отладочных данных, создаваемых для проекта.<br /><br /> По умолчанию установлен формат /ZI, означающий создание базы данных программы (PDB) в формате, совместимом с операцией "Изменить и продолжить". Дополнительные сведения см. в разделе [/Z7,/Zd,/Zi,/Zi (формат отладочной информации)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Папка "C/C++" (категория "Оптимизация")  
  
|Параметр|Описание|  
|-------------|-----------------|  
|**Optimization**|Указывает, должен ли компилятор оптимизировать создаваемый им код. При оптимизации исполняемый код изменяется. Оптимизированный код не совпадает в точности с исходным кодом. Это усложняет отладку.<br /><br /> Параметр по умолчанию (**отключено (/0D**) подавляет оптимизацию. Можно производить разработку при отключенной оптимизации и включить оптимизацию только при создании рабочей версии программы.|  
  
### <a name="linker-folder-debugging-category"></a>Папка "Компоновщик" (категория "Отладка")  
  
|Параметр|Описание|  
|-------------|-----------------|  
|**Создавать отладочную информацию** ([/DEBUG](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Указывает компоновщику необходимость включать сведения, формат которых задается ключом /Z7, /Zd, Zi или /ZI.|  
|**Создавать файл базы данных программы** ([/PDB:name](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|В этом поле вводится имя PDB-файла. Должен быть выбран формат отладочной информации ZI или /Zi.|  
|**Удалить закрытые символы** ([/PDBSTRIPPED:filename](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|В этом поле задается имя PDB-файла в том случае, если в PDB-файл не должны выводиться закрытые символы. Этот параметр создает второй файл базы данных программы (PDB) при сборке образа программы с любыми параметрами компилятора или компоновщика, при которых создается PDB-файл (такими как /DEBUG, /Z7, /Zd или /Zi). Второй PDB-файл не содержит символов, которые нежелательно передавать клиентам. Дополнительные сведения см. в разделе [/PDBSTRIPPED (чередование закрытых символов)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Создавать файл сопоставления** ([/MAP](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Указывает компоновщику на необходимость создания файла сопоставления во время компоновки. По умолчанию выбрано значение "Нет". Дополнительные сведения см. в разделе [Параметр /MAP (создание файла сопоставления)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Имя файла сопоставления** ([/MAP:](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*имя*)|Если выбрано создание файла сопоставления, в этом поле можно указать имя файла сопоставления. Дополнительные сведения см. в разделе [Параметр /MAP (создание файла сопоставления)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Сопоставлять экспортируемые функции** ([/MAPINFO:EXPORTS](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Включение экспортируемых функций в файл сопоставления. По умолчанию выбрано значение "Нет". См. сведения в описании аргумента [/MAPINFO (включение сведений в файл сопоставления)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Отлаживаемая сборка** ([/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Задает параметры для параметра компоновщика /ASSEMBLYDEBUG. Возможные значения:<br /><br /> -   **Атрибут Debuggable не порождается**.<br />-   **Отслеживание во время выполнения и отключение оптимизации (/ASSEMBLYDEBUG)** . Это значение установлено по умолчанию.<br />-   **Нет отслеживания во время выполнения и отключения оптимизации (/ASSEMBLYDEBUG:DISABLE)** .<br />-   **\<inherit from parent or project defaults>**.<br />— Дополнительные сведения см. в разделе [Параметр /ASSEMBLYDEBUG (добавление атрибута DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Эти параметры в папке "Свойства конфигурации" (категория "Отладка") можно изменить программным путем с помощью интерфейса Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Для получения дополнительной информации см. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>См. также:  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Создание проектов Visual C++ и управление ими](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (Добавление DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Стандартные макросы для команд и свойств сборки](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)
