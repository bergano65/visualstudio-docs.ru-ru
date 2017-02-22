---
title: "Параметры проекта для конфигурации отладки C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "PDB-файлы, параметры проекта отладочного построения"
  - "/DEBUG - параметр компоновщика"
  - "/MAP - параметр компоновщика"
  - "/MAPINFO - параметр компоновщика"
  - "/PDB - параметр компоновщика"
  - "/PDBSTRIPPED - параметр компоновщика"
  - "/Z7 - параметр компилятора [C++]"
  - "/Zd - параметр компилятора [C++]"
  - "/ZI - параметр компилятора [C++]"
  - "отладочные построения, параметры проекта"
  - "конфигурации отладки, C++"
  - "DEBUG - параметр компоновщика"
  - "-DEBUG - параметр компоновщика"
  - "отладка [C++], параметров отладчика"
  - "MAP - параметр компоновщика"
  - "-MAP - параметр компоновщика"
  - "файлы сопоставления, параметры проекта"
  - "MAPINFO - параметр компоновщика"
  - "-MAPINFO - параметр компоновщика"
  - "PDB-файлы, параметры проекта отладочного построения"
  - "PDB - параметр компоновщика"
  - "-PDB - параметр компоновщика"
  - "PDBSTRIPPED - параметр компоновщика"
  - "-PDBSTRIPPED - параметр компоновщика"
  - "конфигурации проектов, отладка"
  - "параметры проекта [Visual Studio]"
  - "параметры проекта [Visual Studio], конфигурации отладки"
  - "проекты [Visual Studio], конфигурации отладки"
  - "Z7 - параметр компилятора [C++]"
  - "-Z7 - параметр компилятора [C++]"
  - "Zd - параметр компилятора [C++]"
  - "-Zd - параметр компилятора [C++]"
  - "ZI - параметр компилятора [C++]"
  - "-Zl - параметр компилятора [C++]"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Параметры проекта для конфигурации отладки C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно изменить параметры проекта для отладочной конфигурации C или Visual C\+\+ в диалоговом окне **Страницы свойств**, как описано в разделе [Практическое руководство. Настройка конфигураций отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  В следующих таблицах показано, где в диалоговом окне **Страницы свойств** можно найти параметры, связанные с отладчиком.  
  
> [!WARNING]
>  Параметры отладки проекта в категории **Свойства конфигурации\/Отладка** для приложений для Магазина Windows и компонентов, написанных на C\+\+, будут другими.  См. раздел [Запуск сеанса отладки \(VB, C\#, C\+\+ и XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) в Центре разработки для Windows.  
  
 Укажите используемый отладчик в списке **Загружаемый отладчик**.  В зависимости от выбора, будут отображены те или иные свойства.  
  
 При сохранении решения каждый параметр свойств, связанных с отладкой, автоматически записывается и сохраняется в индивидуальном пользовательском файле \(.vcxproj.user\) для данного решения.  
  
### Папка "Свойства конфигурации" \(категория "Отладка"\)  
  
|**Параметр**|**Описание**|  
|------------------|------------------|  
|**Загружаемый отладчик**|Позволяет выбрать отладчик для запуска из следующих вариантов:<br /><br /> -   **Локальный отладчик Windows**<br />-   **Удаленный отладчик Windows**<br />-   **Отладчик веб\-браузера**<br />-   **Отладчик веб\-служб**|  
|**Команда** \(локальный отладчик Windows\)|Задает команду для запуска отлаживаемой программы на локальном компьютере.|  
|**Удаленная команда** \(удаленный отладчик Windows\)|Путь к EXE\-файлу на удаленном компьютере.  Путь следует вводить в том же виде, в каком он вводился бы на удаленном компьютере.|  
|**Аргументы команды** \(локальный отладчик Windows и удаленный отладчик Windows\)|-   Задает аргументы для указанной выше команды.<br /><br /> В этом поле можно использовать следующие операторы перенаправления:<br /><br /> \< `file`<br /> Чтение потока stdin из файла.<br /><br /> \> `file`<br /> Запись потока stdout в файл.<br /><br /> \>\> `file`<br /> Добавление потока stdout в файл.<br /><br /> 2\> `file`<br /> Запись потока stderr в файл.<br /><br /> 2\>\> `file`<br /> Добавление потока stderr в файл.<br /><br /> 2\> &1<br /> Перенаправление вывода потока stderr \(2\) в то же место назначения, что и у потока stdout \(1\).<br /><br /> 1\> &2<br /> Перенаправление вывода потока stdout \(1\) в то же место назначения, что и у потока stderr \(2\).<br /><br /> В большинстве случаев эти операторы применимы только для консольных приложений.|  
|**Рабочая папка**|Указывает рабочий каталог отлаживаемой программы относительно каталога проекта, в котором расположен исполняемый EXE\-файл.  Если оставить это поле пустым, каталогом проекта будет являться рабочий каталог.  При удаленной отладке каталог проекта располагается на удаленном сервере.|  
|**Присоединиться** \(локальный отладчик Windows и удаленный отладчик Windows\)|Указывает, запускать ли приложение или выполнять присоединение к этому приложению.  По умолчанию выбрано значение "Нет".|  
|**Имя удаленного сервера** \(удаленный отладчик Windows\)|Задает имя компьютера \(не вашего\), на котором предполагается производить отладку приложения.<br /><br /> Макрос сборки "RemoteMachine" принимает значение этого свойства. Дополнительные сведения см. в разделе [Макрос для команд и свойств сборки](/visual-cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Подключение** \(удаленный отладчик Windows\)|Выбор типа подключения для удаленной отладки: стандартное подключение или подключение без аутентификации.  Укажите имя удаленного компьютера в поле **Имя удаленного сервера**.  Доступны следующие типы подключения:<br /><br /> -   **Удаленный доступ с аутентификацией Windows**<br />-   **Удаленный доступ без аутентификации Windows \(только машинный код\)**<br /><br /> **Примечание.** При удаленной отладке без аутентификации удаленный компьютер может стать уязвимым с точки зрения безопасности.  Режим аутентификации Windows является более безопасным.<br /><br /> Дополнительные сведения см. в разделе [Установка удаленной отладки](../debugger/remote-debugging.md).|  
|**HTTP URL** \(отладчик веб\-служб и отладчик веб\-браузера\)|Указывает URL\-адрес, по которому расположен отлаживаемый проект.|  
|**Тип отладчика**|Указывает тип используемого отладчика: **Только машинный код**, **Только управляемый код**, **Только графический процессор**, **Смешанный код**, **Авто** \(по умолчанию\) или **Скрипт**.<br /><br /> -   **Только машинный код** — используется для неуправляемого кода C\+\+.<br />-   **Только управляемый код** — используется для кода, выполняемого в среде CLR \(управляемого кода\).<br />-   **Смешанный код** — вызывает отладчики как для управляемого, так и для неуправляемого типов кода.<br />-   **Авто** — определяет тип отладчика на основании информации компилятора и исполняемого файла.<br />-   **Скрипт** — вызывает отладчик для скриптов.<br />-   **Только графический процессор** — для кода C\+\+ AMP, который выполняется на устройстве GPU или на средстве программной прорисовки DirectX.  Подробнее см. раздел [Отладка кода GPU](../debugger/debugging-gpu-code.md).|  
|**Среда** \(локальный отладчик Windows\)|Указывает переменные среды для отлаживаемой программы.  Используйте стандартный синтаксис переменной среды \(например, `PATH="%SystemRoot%\..."`\).  Эти переменные переопределяют системную среду или объединяются с ее переменными, в зависимости от значения параметра **Объединение среды**.  Если щелкнуть по столбцу параметров, появится элемент "Изменить...".  Щелкните эту ссылку, чтобы изменить переменные среды.|  
|**Объединение среды** \(локальный отладчик Windows\)|Определяет, будут ли переменные, указанные в поле **Среда**, объединяться с переменными среды, определяемыми операционной системой.  По умолчанию выбрано значение "Да".|  
|**Отладка SQL** \(все, за исключением отладчика MPI\-кластера\)|Включает отладку SQL\-процедур из приложения [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  По умолчанию выбрано значение "Нет".|  
|**Тип ускорителя отладки** \(только для отладки GPU\)|Указывает устройство GPU для отладки.  При установке драйверов устройств для совместимых устройств GPU добавляются дополнительные параметры.  По умолчанию установлено значение "Программный эмулятор GPU".|  
|**Стандартное поведение точек останова для GPU** \(только для отладки GPU\)|Указывает, должно ли событие точки останова вызываться для каждого потока в варпе SIMD.  По умолчанию выбран однократный вызов события точки останова для каждого варпа.|  
|**Ускоритель по умолчанию для AMP** \(только для отладки GPU\)|Определяет ускоритель, по умолчанию используемый для AMP при отладке кода GPU.  Выберите **WARP software accelerator**, чтобы выяснить, вызвана ли проблема оборудованием или драйвером, а не кодом.|  
|**Каталог развертывания** \(удаленный отладчик Windows\)|Задает путь на удаленном компьютере, куда будут копироваться выходные данные проекта перед запуском.  Путь может быть сетевой папкой на удаленном компьютере, либо это может быть путь к папке на удаленном компьютере.  По умолчанию это поле пусто, что означает, что выходные данные проекта не копируются в сетевую папку.  Чтобы включить развертывание файлов, необходимо также установить флажок **Развертывание** в диалоговом окне Диспетчера конфигураций.  Дополнительные сведения см. в разделе [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).|  
|**Дополнительные файлы развертывания** \(удаленный отладчик Windows\)|Если в поле "Каталог развертывания" задан каталог развертывания, в этом поле указывается список дополнительных файлов \(разделяемых точкой с запятой\), которые должны копироваться в каталог развертывания.  По умолчанию это поле пусто, что означает, что никакие дополнительные файлы в каталог развертывания не копируются.  Чтобы включить развертывание файлов, необходимо также установить флажок **Развертывание** в диалоговом окне Диспетчера конфигураций.  Дополнительные сведения см. в разделе [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).|  
|**Развертывание отладочных библиотек времени выполнения Visual C\+\+** \(удаленный отладчик Windows\)|Если в поле "Каталог развертывания" задан каталог развертывания, данный параметр указывает, должны ли библиотеки времени выполнения отладки Visual C\+\+ для текущей платформы копироваться в сетевую папку.  Значением по умолчанию является "Да".|  
  
### Папка "C\/C\+\+" \(категория "Общие"\)  
  
|Параметр|Описание|  
|--------------|--------------|  
|**Формат отладочной информации** \([\/Z7, \/Zd, Zi, \/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|Указывает тип отладочных данных, создаваемых для проекта.<br /><br /> По умолчанию установлен формат \/ZI, означающий создание базы данных программы \(PDB\) в формате, совместимом с операцией "Изменить и продолжить".  Дополнительные сведения см. в разделе [\/Z7, \/Zd, \/Zi, \/ZI \(формат отладочной информации\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
### Папка "C\/C\+\+" \(категория "Оптимизация"\)  
  
|Параметр|Описание|  
|--------------|--------------|  
|**Оптимизация**|Указывает, должен ли компилятор оптимизировать создаваемый им код.  При оптимизации исполняемый код изменяется.  Оптимизированный код не совпадает в точности с исходным кодом.  Это усложняет отладку.<br /><br /> По умолчанию установлено значение **Отключено \(\/0D\)**, то есть оптимизация не производится.  Можно производить разработку при отключенной оптимизации и включить оптимизацию только при создании рабочей версии программы.|  
  
### Папка "Компоновщик" \(категория "Отладка"\)  
  
|Параметр|Описание|  
|--------------|--------------|  
|**Создавать отладочную информацию** \([\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)\)|Указывает компоновщику необходимость включать сведения, формат которых задается ключом \/Z7, \/Zd, Zi или \/ZI.|  
|**Создавать файл базы данных программы** \([\/PDB:](/visual-cpp/build/reference/pdb-use-program-database)\)|В этом поле вводится имя PDB\-файла.  Должен быть выбран формат отладочной информации ZI или \/Zi.|  
|**Удалить закрытые символы** \([\/PDBSTRIPPED:FILENAME](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|В этом поле задается имя PDB\-файла в том случае, если в PDB\-файл не должны выводиться закрытые символы.  Этот параметр создает второй файл базы данных программы \(PDB\) при сборке образа программы с любыми параметрами компилятора или компоновщика, при которых создается PDB\-файл \(такими как \/DEBUG, \/Z7, \/Zd  или \/Zi\).  Второй PDB\-файл не содержит символов, которые нежелательно передавать клиентам.  Дополнительные сведения см. в разделе [\/PDBSTRIPPED \(удалить закрытые символы\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Создавать файл сопоставления** \([\/MAP](/visual-cpp/build/reference/map-generate-mapfile)\)|Указывает компоновщику на необходимость создания файла сопоставления во время компоновки.  По умолчанию выбрано значение "Нет".  Дополнительные сведения см. в разделе [\/MAP \(создание файла сопоставления\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Имя файла сопоставления** \([\/MAP:](/visual-cpp/build/reference/map-generate-mapfile)*имя*\)|Если выбрано создание файла сопоставления, в этом поле можно указать имя файла сопоставления.  Дополнительные сведения см. в разделе [\/MAP \(создание файла сопоставления\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Сопоставлять экспортируемые функции** \([\/MAPINFO:EXPORTS](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Включение экспортируемых функций в файл сопоставления.  По умолчанию выбрано значение "Нет".  Дополнительные сведения см. в разделе [\/MAPINFO \(включение данных в файл сопоставления\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Отлаживаемая сборка** \([\/ASSEMBLYDEBUG](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Задает параметры для параметра компоновщика \/ASSEMBLYDEBUG.  Ниже приведены возможные значения.<br /><br /> -   **Атрибут Debuggable не порождается**.<br />-   **Отслеживание во время выполнения и отключение оптимизации \(\/ASSEMBLYDEBUG\)**.  Это значение установлено по умолчанию.<br />-   **Нет отслеживания во время выполнения и отключения оптимизации \(\/ASSEMBLYDEBUG:DISABLE\)**.<br />-   **\<наследовать от родителя или от значений по умолчанию для проекта\>**.<br />-   Дополнительные сведения см. в разделе [\/ASSEMBLYDEBUG \(добавление атрибута DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Эти параметры в папке "Свойства конфигурации" \(категория "Отладка"\) можно изменить программным путем с помощью интерфейса Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings.  Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры отладки и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Создание проектов Visual C\+\+ и управление ими](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(добавление атрибута DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Макросы для команд и свойств построения](/visual-cpp/ide/common-macros-for-build-commands-and-properties)