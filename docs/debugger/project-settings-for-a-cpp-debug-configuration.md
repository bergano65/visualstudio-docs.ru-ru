---
title: Параметры проекта для конфигурации отладки C++
ms.custom: seodec18
ms.date: 11/26/2018
ms.technology: vs-ide-debug
ms.topic: reference
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
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 951b46bfc6ef0910731dfe76cc9913f2c4a423ad
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066906"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Параметры проекта для конфигурации отладки C++
Можно изменить параметры проекта для конфигурации отладки C или Visual C++ в **страницы свойств** диалоговое окно, как описано в [как: настроить отладку и выпуск конфигураций](../debugger/how-to-set-debug-and-release-configurations.md). В следующих таблицах показано, где в диалоговом окне **Страницы свойств** можно найти параметры, связанные с отладчиком.  
  
> [!NOTE]
>  Параметры отладки проекта в **свойства конфигурации/Отладка** категории различаются для приложений универсальной платформы Windows и компонентов, написанных на C++. См. в разделе [начать сеанс отладки (VB, C#, C++ и XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Каждый параметр свойств отладки записывается и сохраняется в файле «на пользователя» (. vcxproj.user) для вашего решения, при сохранении решения.  

 Укажите используемый отладчик в **отладчик для запуска** поле со списком, как описано в следующей таблице. В зависимости от выбора, будут отображены те или иные свойства.  
    
## <a name="configuration-properties-folder-debugging-category"></a>Папка "Свойства конфигурации" (категория "Отладка")  
  
| **Параметр** | **Описание** |
| - | - |
| **Отладчик для запуска** | Позволяет выбрать отладчик для запуска из следующих вариантов:<br /><br /> -   **Локальный отладчик Windows**<br />-   **Удаленный отладчик Windows**<br />-   **Отладчик веб-браузера**<br />-   **Отладчик веб-служб** |
| **Команда** (локальный отладчик Windows) | Задает команду для запуска отлаживаемой программы на локальном компьютере. |
| **Удаленная команда** (удаленный отладчик Windows) | Путь к EXE-файлу на удаленном компьютере. Путь следует вводить в том же виде, в каком он вводился бы на удаленном компьютере. |
| **Аргументы команды** (отладчик локального Windows)<br /><br /> **Аргументы удаленной команды** (Windows, удаленный отладчик) | — Задает аргументы для указанной выше команды.<br /><br /> В этом поле можно использовать следующие операторы перенаправления:<br /><br /> < `file`<br /> Чтение потока stdin из файла.<br /><br /> > `file`<br /> Запись потока stdout в файл.<br /><br /> >> `file`<br /> Добавление потока stdout в файл.<br /><br /> 2> `file`<br /> Запись потока stderr в файл.<br /><br /> 2>> `file`<br /> Добавление потока stderr в файл.<br /><br /> 2> &1<br /> Перенаправление вывода потока stderr (2) в то же место назначения, что и у потока stdout (1).<br /><br /> 1> &2<br /> Перенаправление вывода потока stdout (1) в то же место назначения, что и у потока stderr (2).<br /><br /> В большинстве случаев эти операторы применимы только для консольных приложений. |
| **Рабочий каталог** | Указывает рабочий каталог отлаживаемой программы относительно каталога проекта, в котором расположен исполняемый EXE-файл. Если оставить это поле пустым, каталогом проекта будет являться рабочий каталог. Для удаленной отладки каталог проекта находится на удаленном сервере. |
| **Присоединиться** (локальный отладчик Windows и удаленный отладчик Windows) | Указывает, запускать ли приложение или выполнять присоединение к этому приложению. По умолчанию выбрано значение "Нет". |
| **Имя удаленного сервера** (удаленный отладчик Windows) | Задает имя компьютера (не вашего), на котором предполагается производить отладку приложения.<br /><br /> Макрос сборки "RemoteMachine" принимает значение этого свойства. Дополнительные сведения см. в разделе [Макрос для команд и свойств сборки](/cpp/ide/common-macros-for-build-commands-and-properties). |
| **Подключение** (удаленный отладчик Windows) | Выбор типа подключения для удаленной отладки: стандартное подключение или подключение без аутентификации. Укажите имя удаленного компьютера в поле **Имя удаленного сервера**. Доступны следующие типы подключения:<br /><br /> -   **Удаленный доступ с проверкой подлинности Windows**<br />-   **Удаленный доступ без проверки подлинности**<br /><br /> **Примечание.** При удаленной отладке без проверки подлинности удаленный компьютер может стать уязвимым с точки зрения безопасности. Режим аутентификации Windows является более безопасным.<br /><br /> Дополнительные сведения см. в разделе [Настройка удаленной отладки](../debugger/remote-debugging.md). |
| **URL-адрес HTTP** (отладчик веб-служб и отладчик веб-браузера) | Указывает URL-адрес, по которому расположен отлаживаемый проект. |
| **Тип отладчика** | Указывает тип отладчика: **Только машинный код**, **только управляемый код**, **только графический Процессор**, **Mixed**, **автоматически** (по умолчанию), или **скрипт**.<br /><br /> -   **Только машинный код** — используется для неуправляемого кода C++.<br />-   **Только управляемый код** — используется для кода, выполняемого в среде CLR (управляемого кода).<br />-   **Смешанный код** — вызывает отладчики как для управляемого, так и для неуправляемого типов кода.<br />-   **Авто** — определяет тип отладчика на основании информации компилятора и исполняемого файла.<br />-   **Скрипт** — вызывает отладчик для скриптов.<br />-   **Только графический процессор** — для кода C++ AMP, который выполняется на устройстве GPU или на средстве программной прорисовки DirectX. См. в разделе [код отладки GPU](../debugger/debugging-gpu-code.md). |
| **Среда** (отладчик локального Windows и Windows, удаленный отладчик) | Указывает переменные среды для отлаживаемой программы. Используйте стандартный синтаксис переменной среды (например, `PATH="%SystemRoot%\..."`). Эти переменные переопределяют системную среду или объединяются с ее переменными, в зависимости от значения параметра **Объединение среды**. Когда вы щелкните левой кнопкой мыши по столбцу параметров, появится элемент «изменить...». Выберите эту ссылку, чтобы изменить переменные среды. |
| **Объединение среды** (локальный отладчик Windows) | Определяет, будут ли переменные, указанные в поле **Среда**, объединяться со средой, определяемой операционной системой. По умолчанию выбрано значение "Да". |
| **Отладка SQL** (все, за исключением отладчика MPI-кластера) | Включает отладку SQL-процедур из приложения [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. По умолчанию выбрано значение "Нет". |
| **Тип ускорителя отладки** (только для отладки GPU) | Указывает устройство GPU для отладки. При установке драйверов устройств для совместимых устройств GPU добавляются дополнительные параметры. По умолчанию установлено значение **Программный эмулятор GPU**. |
| **Стандартное поведение точек останова для GPU** (только для отладки GPU) | Указывает, должно ли событие точки останова вызываться для каждого потока в варпе SIMD. По умолчанию выбран однократный вызов события точки останова для каждого варпа. |
| **Ускоритель по умолчанию для AMP** | Определяет ускоритель, по умолчанию используемый для AMP при отладке кода GPU. Выберите **Ускоритель ПО WARP**, чтобы выяснить, вызвана ли проблема оборудованием или драйвером, а не кодом. |
| **Каталог развертывания** (удаленный отладчик Windows) | Задает путь на удаленном компьютере, куда будут копироваться выходные данные проекта перед запуском. Путь может быть сетевой папкой на удаленном компьютере, либо это может быть путь к папке на удаленном компьютере. По умолчанию это поле пусто, что означает, что выходные данные проекта не копируются в сетевую папку. Чтобы включить развертывание файлов, нужно также установить флажок **Развертывание** в диалоговом окне "Диспетчер конфигураций". Дополнительные сведения см. в разделе [Как создавать и изменять конфигурации](../ide/how-to-create-and-edit-configurations.md). |
| **Дополнительные файлы развертывания** (удаленный отладчик Windows) | Если задан каталог развертывания, это список разделенных точкой с запятой дополнительные файлы для копирования в каталог развертывания. По умолчанию это поле пусто, что означает, что никакие дополнительные файлы в каталог развертывания не копируются. Чтобы включить развертывание файлов, нужно также установить флажок **Развертывание** в диалоговом окне "Диспетчер конфигураций". Дополнительные сведения см. в разделе [Как создавать и изменять конфигурации](../ide/how-to-create-and-edit-configurations.md). |
| **Развертывание отладочных библиотек времени выполнения Visual C++** (удаленный отладчик Windows) | Если в поле "Каталог развертывания" задан каталог развертывания, данный параметр указывает, должны ли библиотеки времени выполнения отладки Visual C++ для текущей платформы копироваться в сетевую папку. Значением по умолчанию является "Да". |
  
## <a name="cc-folder-general-category"></a>Папка "C/C++" (категория "Общие")  
  
|Параметр|Описание|  
|-------------|-----------------|  
|**Формат отладочной информации** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Указывает тип отладочных данных, создаваемых для проекта.<br /><br /> По умолчанию установлен формат /ZI, означающий создание базы данных программы (PDB) в формате, совместимом с операцией "Изменить и продолжить". Дополнительные сведения см. в разделе [/Z7, /Zd, /Zi, /ZI (формат отладочной информации)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Папка "C/C++" (категория "Оптимизация")  
  
|Параметр|Описание|  
|-------------|-----------------|  
|**Optimization**|Указывает, должен ли компилятор оптимизировать создаваемый им код. При оптимизации исполняемый код изменяется. Оптимизированный код не соответствует исходный код, что затрудняет отладку.<br /><br /> По умолчанию установлено значение **Отключено (/0d)**, то есть оптимизация не производится. Можно производить разработку при отключенной оптимизации и включить оптимизацию только при создании рабочей версии программы.|  
  
## <a name="linker-folder-debugging-category"></a>Папка "Компоновщик" (категория "Отладка")  
  
|Параметр|Описание:|  
|-------------|-----------------|  
|**Создавать отладочную информацию** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Указывает компоновщику включать сведения, формат которых задается ключом [/Z7, /Zd, Zi или /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
|**Создавать файл базы данных программы** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Укажите имя файла базы данных (PDB) программы в этом окне. Должен быть выбран формат отладочной информации ZI или /Zi.|  
|**Удалить закрытые символы** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|В этом поле задается имя PDB-файла в том случае, если в PDB-файл не должны выводиться закрытые символы. Этот параметр создает второй файл PDB-ФАЙЛ при построении образа программы с любыми параметрами компилятора или компоновщика, создающими файл PDB-файла, например/Debug, / Z7, / Zd. или /Zi). Второй PDB-файл не содержит символов, которые нежелательно передавать клиентам. Дополнительные сведения см. в разделе [/PDBSTRIPPED (пропуск частных символов)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Создавать файл сопоставления** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Указывает компоновщику на необходимость создания файла сопоставления во время компоновки. По умолчанию выбрано значение "Нет". Дополнительные сведения см. в разделе [Параметр /MAP (создание файла сопоставления)](/cpp/build/reference/map-generate-mapfile).|  
|**Имя файла сопоставления** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*имя*)|Если выбрано создание файла сопоставления, в этом поле можно указать имя файла сопоставления. Дополнительные сведения см. в разделе [Параметр /MAP (создание файла сопоставления)](/cpp/build/reference/map-generate-mapfile).|  
|**Сопоставлять экспортируемые функции** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Включение экспортируемых функций в файл сопоставления. По умолчанию выбрано значение "Нет". Дополнительные сведения см. в разделе [/MAPINFO (Включение сведений в файл сопоставления)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Отлаживаемая сборка** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Задает параметры для параметра компоновщика /ASSEMBLYDEBUG. Доступны следующие значения:<br /><br /> -   **Атрибут Debuggable не порождается**.<br />-   **Отслеживание во время выполнения и отключение оптимизации (/ASSEMBLYDEBUG)**. Это значение установлено по умолчанию.<br />-   **Нет отслеживания во время выполнения и отключения оптимизации (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<наследовать от родителя или от значений по умолчанию для проекта>**.<br />— Дополнительные сведения см. в разделе [Параметр /ASSEMBLYDEBUG (добавление атрибута DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Эти параметры в папке "Свойства конфигурации" (категория "Отладка") можно изменить программным путем с помощью интерфейса Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Другие параметры проекта

Отладка типов проектов, например статических библиотек и библиотек DLL, проект Visual Studio должен иметь возможность найти нужные файлы. Если исходный код доступен, можно добавить статические библиотеки и библиотеки DLL как отдельные проекты в то же решение, чтобы упростить отладку. Сведения о создании этих типов проектов, см. в разделе [Создание и использование библиотеки динамических ссылок (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) и [Создание статической библиотеки с помощью](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). С исходным кодом доступен, можно также создать новый проект Visual Studio, выбрав **файл** > **New** > **проект из существующего кода**.

Чтобы выполнить отладку библиотеки DLL, которые являются внешними по отношению к проекту, см. в разделе [проектов DLL, отладка](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Если требуется отладка DLL проекта, но не имеют доступ к проекту для вызывающего приложения, см. в разделе [как выполнить отладку из проекта DLL](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Создание и управление проектами Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ASSEMBLYDEBUG (добавление атрибута DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Стандартные макросы для команд и свойств сборки](/cpp/ide/common-macros-for-build-commands-and-properties)