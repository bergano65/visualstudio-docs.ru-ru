---
title: "При установке приложения изолированной оболочки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Развертывание приложений на основе командной оболочки [Visual Studio]"
  - "Оболочка Visual Studio, развертывание приложений на основе оболочки"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 40
---
# При установке приложения изолированной оболочки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для установки приложения оболочки необходимо выполнить следующие действия.  
  
-   Подготовка решения.  
  
-   Создание пакета установщика Windows \(MSI\) для вашего приложения.  
  
-   Создайте файл\-загрузчик программы установки.  
  
 Весь код примера в этом документе поступают из [Пример развертывания оболочки](http://go.microsoft.com/fwlink/?LinkId=262245), который можно загрузить из коллекции кода на веб\-сайте MSDN. В этом примере результаты выполнения этих этапов.  
  
## Необходимые компоненты  
 Для выполнения процедур, описанных в этом разделе, следующие средства необходимо установить на компьютере.  
  
-   Пакет SDK для Visual Studio  
  
-   [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) версии 3.6  
  
 Образец также требуется Microsoft визуализации и моделирования пакет SDK, который требуется не для всех интерпретаторов команд.  
  
## Подготовка решения  
 По умолчанию построение оболочки шаблоны для пакетов VSIX, но это поведение предусмотрено в первую очередь для отладки. При развертывании приложения оболочки, необходимо использовать пакеты MSI разрешение для доступа к реестру и при перезагрузке в процессе установки. Подготовка приложения для развертывания MSI\-ФАЙЛ, выполните следующие действия.  
  
#### Чтобы подготовить приложение оболочки для развертывания MSI  
  
1.  Измените каждый файл .vsixmanifest в решении.  
  
     В `Identifier` элемента, добавьте `InstalledByMSI` элемент и `SystemComponent` элемент и затем задайте их значения `true`.  
  
     Эти элементы не пытался установить компоненты и пользователя из их удаление с помощью установщик VSIX **расширения и обновления** диалоговое окно.  
  
2.  Для каждого проекта, содержащего манифест VSIX измените задачи построения для вывода содержимого для расположения, из которого будет производиться установка MSI\-ФАЙЛЕ. Включить манифест VSIX в выходные данные построения, но не создавайте VSIX\-файл.  
  
## Создание MSI\-ФАЙЛ для своей оболочки  
 Для создания пакета MSI, мы рекомендуем использовать [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) так как он обеспечивает большую гибкость, чем стандартный проект установки.  
  
 В файле Product.wxs набор блоков определения и макет компонентов оболочки.  
  
 Создайте записи реестра в REG\-файл для решения и в ApplicationRegistry.wxs.  
  
### Обнаружение блоков  
 Обнаружение блок состоит из `Property` элемент, указывающий необходимым условием для обнаружения и `Condition` элемент, который задает сообщение об ошибке, если на компьютере отсутствует обязательный компонент. Например приложению оболочки потребуется распространяемый пакет оболочки Microsoft Visual Studio и обнаружения блока будет напоминать следующую разметку.  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### Макет компонента оболочки  
 Необходимо добавить элементы для определения структуры каталогов и компоненты для установки.  
  
##### Чтобы задать макет компонентов оболочки  
  
1.  Создать иерархию `Directory` элементов для представления всех каталогов, чтобы создать файловую систему на конечном компьютере, как показано в следующем примере.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     Эти каталоги, обозначенные `Id` Если указаны файлы, которые должны быть установлены.  
  
2.  Определение компонентов, необходимых для оболочки и оболочки приложения, как показано в следующем примере.  
  
    > [!NOTE]
    >  Некоторые элементы могут ссылаться на определения в других файлах .wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  `ComponentRef` Элемент содержит ссылку на другой WXS\-файл, который определяет файлы, необходимые для текущего компонента. Например GeneralProfile имеет следующее определение в HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         `DirectoryRef` Элемент указывает, куда эти файлы на компьютере пользователя.`Directory` Элемент указывает, что он будет установлен в подкаталог, а каждый `File` элемент представляет файл, построенный или существует как часть решения и определяет, где этот файл можно получить при создании MSI\-файл.  
  
    2.  `ComponentGroupRef` Элемент относится к группе другими компонентами \(или компоненты и группы компонентов\). Например `ComponentGroupRef` под ApplicationGroup определяется следующим образом в Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Зависимостей для приложений, оболочка \(изолированная\) являются: DebuggerProxy, MasterPkgDef, ресурсы \(особенно .winprf\-файл\), приложения и PkgDefs.  
  
### Записи реестра  
 Шаблон проекта Shell \(изолированный режим\) включает *ProjectName*REG\-файл для разделов реестра для слияния при установке. Эти записи реестра должны быть частью MSI\-ФАЙЛ для установки и очистки в целях. Также необходимо создать соответствующие блоки реестра в ApplicationRegistry.wxs.  
  
##### Интеграция записи реестра в MSI\-ФАЙЛ  
  
1.  В **настроек оболочки** откройте *ProjectName*. reg.  
  
2.  Замените все экземпляры маркер $ $RootFolder путь к целевой каталог установки.  
  
3.  Добавьте другие записи реестра, которые требуются приложению.  
  
4.  Откройте ApplicationRegistry.wxs.  
  
5.  Для каждой записи реестра в *ProjectName*файл с расширением REG, добавьте соответствующий блок реестра, как в приведенных ниже примерах.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= «Объект PhotoStudio DTE»|\< RegistryKey Id \= «DteClsidRegKey» корневой \= «HKCR» Key \= "$\(var. DteClsidRegKey\) "Action \="createAndRemoveOnUninstall"\><br /><br /> \< тип RegistryValue \= «строка» Name \= "@" значение \= "$\(var. Объект ShortProductName\) DTE "\/ \><br /><br /> \< \/ RegistryKey \>|  
    |\[\\LocalServer32 HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= «$RootFolder$\\PhotoStudio.exe»|\< RegistryKey Id \= «DteLocSrv32RegKey» корневой \= «HKCR» Key \= "$\(var. DteClsidRegKey\) \\LocalServer32 "Action \="createAndRemoveOnUninstall"\><br /><br /> \< тип RegistryValue \= «строка» Name \= "@" значение \= "\[INSTALLDIR\] $\(var. ShortProductName\) .exe "\/ \><br /><br /> \< \/ RegistryKey \>|  
  
     В этом примере разрешает Var.DteClsidRegKey раздел реестра в верхней строке. Разрешает Var.ShortProductName `PhotoStudio`.  
  
## Создание загрузчика программы установки  
 Завершенный MSI\-ФАЙЛЕ будет установлен только в том случае, если сначала установить все необходимые компоненты. Чтобы упростить взаимодействие с пользователем, создайте программу установки, которая собирает и устанавливает все необходимые компоненты перед установкой приложения. Для успешной установки, выполните следующие действия.  
  
-   Принудительной установки администратором.  
  
-   Проверяет, установлена ли оболочка Visual Studio \(изолированная\).  
  
-   Чтобы запустите установщики оболочки один или оба.  
  
-   Обрабатывать запросы на перезапуск.  
  
-   Запустите MSI\-ФАЙЛЕ.  
  
### Принудительное выполнение установки администратором  
 Эту процедуру необходимо включить обязательные каталоги, например \\Program Files\\ доступ к программе установки.  
  
##### Для принудительной установки администратором  
  
1.  Откройте контекстное меню для проекта установки и выберите **Свойства**.  
  
2.  В разделе **компоновщика\/свойства\/манифест файла конфигурации**, задайте **уровень выполнения UAC** для **requireAdministrator**.  
  
     Это свойство помещает атрибута, который требуется программа для запуска от имени администратора в внедренный файл манифеста.  
  
### Обнаружение установки оболочки  
 Чтобы определить, установлен ли оболочка Visual Studio \(изолированная\), сначала определить, уже установлены ли путем проверки значения реестра HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install.  
  
> [!NOTE]
>  Эти значения также считываются в Product.wxs блоком обнаружения оболочки.  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder Указывает расположение, где была установлена оболочка Visual Studio, и вы можете искать файлы.  
  
 Пример обнаружения установки оболочки см `GetProductDirFromReg` функции Utilities.cpp в образце развертывания оболочки.  
  
 Если на компьютере не установлен один или оба из Visual Studio оболочек, требующее вашего пакета, необходимо добавить их в список устанавливаемых компонентов. Например, в разделе `ComponentsPage::OnInitDialog` функции ComponentsPage.cpp в образце развертывания оболочки.  
  
### Выполнение оболочки установщиков  
 Для запуска установщиков оболочки, вызовите свободно распространяемые файлы оболочки Visual Studio, используя правильные аргументы командной строки. Как минимум, необходимо использовать аргументы командной строки **\/norestart \/q** и просмотр кода возврата определить, какие действия должны выполняться Далее. В следующем примере выполняется распространяемый пакет оболочки \(изолированный режим\).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### Выполнение установщики оболочки языковой пакет  
 Если вместо этого обнаружится, что установлена оболочка или оболочки и просто требуется языковой пакет, можно установить языковые пакеты, как показано в следующем примере.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### Расшифровка возвращаемые значения  
 В некоторых операционных системах установки оболочки Visual Studio \(изолированный режим\) может потребовать перезагрузки. Это условие можно определить, код возврата вызова `ExecCmd`.  
  
|Возвращаемое значение|Описание|  
|---------------------------|--------------|  
|ERROR\_SUCCESS|Установка завершена. Теперь можно установить приложения.|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|Установка завершена. После перезагрузки компьютера, можно установить приложение.|  
|3015|Установка не завершена. Для продолжения установки требуется перезагрузка компьютера.|  
  
### Обработка перезапуска  
 При запуске установщика оболочки с помощью **\/norestart** вы указан аргумент, не перезагрузить компьютер, или запросить необходимо перезагрузить компьютер. Тем не менее может потребоваться перезагрузить компьютер, и необходимо убедиться, что установщик продолжается после перезагрузки компьютера.  
  
 Для правильной обработки перезагрузки, убедитесь в том, что только одна программа установки задано, возобновление и что процесс возобновления будут обработаны правильно.  
  
 Если возвращается ERROR\_SUCCESS\_REBOOT\_REQUIRED или 3015 кода необходимо перезапустить компьютер перед продолжением установки.  
  
 Обрабатывать перезагрузки, выполните следующие действия.  
  
-   Настройка реестра, чтобы продолжить установку при запуске Windows.  
  
-   Выполните перезагрузку double загрузчика.  
  
-   Удалите ключ ResumeData установщика оболочки.  
  
-   Перезагрузите Windows.  
  
-   Сброс начала путь к MSI\-ФАЙЛ.  
  
### Параметр реестра, чтобы продолжить установку при запуске Windows  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ Реестра выполняется при запуске системы с правами администратора и затем удаляется.HKEY\_CURRENT\_USER содержит как ключ, но он работает как обычный пользователь и не подходит для установки. Можно продолжить установку, поместив строковое значение в раздел RunOnce, который вызывает установщик. Тем не менее, рекомендуется вызвать программу установки с помощью **\/restart** или аналогичный параметр для уведомления, возобновляется вместо запуска приложения. Можно также включить параметры, чтобы указать, где находятся в процесс установки, что особенно полезно в установках, которые может потребоваться несколько перезагрузок.  
  
 Следующий пример показывает RunOnce реестра для возобновления установки.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### Установка Double перезапуска загрузчика  
 При использовании программы установки непосредственно из однократного запуска рабочего стола не сможет загрузить полностью. Для предоставления полного пользовательского интерфейса, необходимо создать другой выполнения программы установки и завершения экземпляра RunOnce.  
  
 Программе установки необходимо выполнить повторно, чтобы он получает правильных разрешений и присвойте ему достаточно информации, чтобы знать, где остановлен перед перезагрузкой, как показано в следующем примере.  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### При удалении ключа ResumeData установщика оболочки  
 Задает установщик оболочки HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData раздел реестра с данными, чтобы возобновить выполнение программы установки после перезагрузки компьютера. Поскольку приложение не установщик оболочки, возобновление, удаление раздела реестра, как показано в следующем примере.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### Перезапуск Windows  
 После выбора требуемых разделов реестра можно перезапустить Windows. В следующем примере вызывается команды перезапуска для разных операционных систем Windows.  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### Сброс путь запуска MSI\-пакета  
 Перед перезагрузкой расположение программы установки используется текущий каталог, но после перезапуска, расположение становится каталог system32. Программе установки необходимо сбросить текущий каталог перед каждым вызовом MSI, как показано в следующем примере.  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### Запуск приложения MSI  
 После возврата ERROR\_SUCCESS установщика оболочки Visual Studio можно запустить MSI\-ФАЙЛ для приложения. Поскольку программа установки предоставляет пользовательский интерфейс, запустите MSI\-ФАЙЛЕ в тихом режиме \(**\/q**\) и с ведением журнала \(**\/L**\), как показано в следующем примере.  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## См. также  
 [Пошаговое руководство: Создание приложения основные изолированной среды](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)