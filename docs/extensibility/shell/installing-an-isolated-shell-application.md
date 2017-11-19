---
title: "При установке приложения изолированной оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afe5ddd5748fe0d8f394a63898370eaf405b3f4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="installing-an-isolated-shell-application"></a>При установке приложения изолированной оболочки
Для установки приложения оболочки необходимо выполнить следующие действия.  
  
-   Подготовка решения.  
  
-   Создайте пакет установщика Windows (MSI) для вашего приложения.  
  
-   Создайте загрузчик программы установки.  
  
 Весь код в этом документе примере берется из [оболочки развертывания образца](http://go.microsoft.com/fwlink/?LinkId=262245), который можно загрузить из галереи кода на веб-сайте MSDN. В этом примере результаты выполнения каждого из следующих действий.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить процедуры, описанные в этом разделе, следующие средства должны устанавливаться на компьютере.  
  
-   Пакет SDK для Visual Studio  
  
-   [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) версии 3.6  
  
 Образец также требуется Microsoft визуализации и моделирования пакета SDK, который требуется не все оболочки.  
  
## <a name="preparing-your-solution"></a>Подготовка решения  
 По умолчанию шаблоны оболочки сборки в пакетах VSIX, но это поведение предназначен главным образом для целей отладки. При развертывании приложения оболочки, чтобы разрешить доступ к реестру и перезагрузка во время установки необходимо использовать MSI-пакетов. Чтобы подготовить приложение для развертывания MSI-ФАЙЛ, выполните следующие действия.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Для подготовки приложения оболочки для развертывания MSI  
  
1.  Изменения каждого файла VSIXMANIFEST в решении.  
  
     В `Identifier` элемента, добавьте `InstalledByMSI` элемент и `SystemComponent` элемент и задайте их значения `true`.  
  
     Эти элементы предотвратить попытки установить компоненты и пользователь с после их удаления с помощью установщик VSIX **расширения и обновления** диалоговое окно.  
  
2.  Для каждого проекта, содержащего манифест VSIX измените задачи построения для вывода содержимого в расположение, из которого будет устанавливать MSI-ФАЙЛЕ. Манифест VSIX включить в выходные данные сборки, но сборка VSIX-файл.  
  
## <a name="creating-an-msi-for-your-shell"></a>Создание MSI-ФАЙЛ для оболочка  
 Для создания пакета MSI, мы рекомендуем использовать [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) потому что он дает большую гибкость, чем стандартная проекта установки.  
  
 В файле Product.wxs набор блоков обнаружения и макет компонентов оболочки.  
  
 Создайте записи реестра в REG-файл для решения и в ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Обнаружение блоков  
 Блок обнаружения состоит из `Property` элемент, который задает необходимого компонента для обнаружения и `Condition` элемент, который задает сообщение для возврата, если необходимый компонент отсутствует на компьютере. Например приложению оболочки потребуется распространяемый пакет оболочки Microsoft Visual Studio и блок обнаружения будет напоминать следующую разметку.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Макет компонентов оболочки  
 Необходимо добавить элементы для определения структуры каталогов и компоненты для установки.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Чтобы задать макет компонентов оболочки  
  
1.  Создать иерархию `Directory` элементов, представляющих все каталоги, чтобы создать файловую систему на конечном компьютере, как показано в следующем примере.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Эти каталоги, обозначенные `Id` при указаны файлы, которые должны быть установлены.  
  
2.  Определение компонентов, необходимых для оболочки и приложения оболочки, как показано в следующем примере.  
  
    > [!NOTE]
    >  Некоторые элементы могут ссылаться на определения в других файлах .wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  `ComponentRef` Элемент ссылается на другой WXS-файл, определяющий файлы, которые требуются для текущего компонента. Например GeneralProfile имеет следующее определение в HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` Элемент указывает, куда эти файлы на компьютере пользователя. `Directory` Элемент указывает, что он будет установлен в подкаталог, а каждый `File` элемент представляет файл, который создан или существует как часть решения и определяет, где этот файл можно получить при создании MSI-файл.  
  
    2.  `ComponentGroupRef` Элемент относится к группе другими компонентами (или компоненты и компоненты группы). Например `ComponentGroupRef` под ApplicationGroup определяется следующим образом в Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Требуется создать необходимые зависимости для приложения оболочки (изолированный): DebuggerProxy MasterPkgDef, ресурсы (особенно .winprf-файл), приложения и PkgDefs.  
  
### <a name="registry-entries"></a>Записи реестра  
 Шаблон проекта оболочки (изолированной) включает в себя *ProjectName*REG-файл для разделов реестра для слияния при установке. Эти записи реестра должны быть частью MSI-ФАЙЛ для установки и очистки в целях. Также необходимо создать соответствующие блоки реестра в ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Для интеграции записи реестра в MSI-ФАЙЛ  
  
1.  В **Настройка оболочки** откройте *ProjectName*. reg.  
  
2.  Замените все экземпляры токена $ $RootFolder путь к каталогу установки целевой.  
  
3.  Добавьте другим записям реестра, которые требуются приложению.  
  
4.  Откройте ApplicationRegistry.wxs.  
  
5.  Для каждой записи реестра в *ProjectName*.reg, добавьте соответствующий блок реестра, как в приведенных ниже примерах.  
  
    |*Имя_проекта*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= «Объект PhotoStudio DTE»|\<RegistryKey Id = «DteClsidRegKey» корневой = «HKCR» Key = "$(var. DteClsidRegKey) "Action = «createAndRemoveOnUninstall» ><br /><br /> \<Тип RegistryValue = 'строка' имя = "@" значение = "$(var. Объект ShortProductName) DTE "/ ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= «$RootFolder$\PhotoStudio.exe»|\<RegistryKey Id = «DteLocSrv32RegKey» корневой = «HKCR» Key = "$(var. \LocalServer32 DteClsidRegKey) "Action = «createAndRemoveOnUninstall» ><br /><br /> \<Тип RegistryValue = 'строка' имя = "@" значение = "[INSTALLDIR] $(var. ShortProductName) .exe "/ ><br /><br /> \</ RegistryKey >|  
  
     В этом примере Var.DteClsidRegKey разрешается в раздел реестра в верхней строке. Разрешает Var.ShortProductName `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Создание загрузчика программы установки  
 Завершенная MSI-ФАЙЛЕ будет устанавливать только в том случае, если сначала установить все необходимые компоненты. Чтобы облегчить взаимодействие с пользователем, создайте программу установки, которая собирает и устанавливает все необходимые компоненты перед установкой приложения. Чтобы обеспечить успешную установку, выполните эти действия.  
  
-   Принудительной установки администратором.  
  
-   Проверяет, установлена ли оболочка Visual Studio (изолированной).  
  
-   Один или оба установщики оболочки выполняются в порядке.  
  
-   Обрабатывает запросы перезапуска.  
  
-   Запустите MSI-ФАЙЛЕ.  
  
### <a name="enforcing-installation-by-administrator"></a>Применение установки администратором  
 Эта процедура необходима для включения программы установки для доступа к требуемые каталоги, например \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Для принудительной установки администратором  
  
1.  Откройте контекстное меню для проекта установки и выберите **свойства**.  
  
2.  В разделе **компоновщика/свойства/манифест файла конфигурации**, задайте **уровень выполнения UAC** для **requireAdministrator**.  
  
     Это свойство помещает атрибут, который требуется для запуска от имени администратора в файле манифеста внедренного программы.  
  
### <a name="detecting-shell-installations"></a>Обнаружение установок оболочки  
 Чтобы определить, необходимо ли устанавливать оболочки Visual Studio (изолированной), сначала определите, ли он уже установлен, проверьте параметр реестра HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Также эти значения считываются в блоке обнаружения оболочки в Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder указывает расположение, где была установлена оболочка Visual Studio, а можно искать файлы.  
  
 Пример того, как для обнаружения установки оболочки см. в разделе `GetProductDirFromReg` функции Utilities.cpp в образце развертывания оболочки.  
  
 Если одно или оба из Visual Studio оболочек, необходимый пакету не установлена на компьютере, необходимо добавить их в список компонентов для установки. Пример см. в разделе `ComponentsPage::OnInitDialog` функции ComponentsPage.cpp в образце развертывания оболочки.  
  
### <a name="running-the-shell-installers"></a>Запуск оболочки установщиков  
 Чтобы запустить установщики оболочки, вызовите свободно распространяемые файлы оболочки Visual Studio, используя правильные аргументы командной строки. Как минимум, необходимо использовать аргументы командной строки **/q/norestart** и просмотр кода возврата определить, какие действия должны выполняться Далее. В следующем примере выполняется распространяемый пакет оболочки (изолированный).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Запуском установщиков оболочки языковой пакет  
 Если вместо этого обнаружится, что оболочка или оболочках были установлены и просто требуется языковой пакет, можно установить языковые пакеты, как показано в следующем примере.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Расшифровки возвращаемого значения  
 В некоторых операционных системах для установки оболочки Visual Studio (изолированной) потребуется перезагрузка. Это условие может определяться код возврата вызова `ExecCmd`.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|ERROR_SUCCESS|Установка завершена. Теперь можно установить приложения.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Установка завершена. После перезагрузки компьютера, можно установить приложения.|  
|3015|Установка не завершена. Для продолжения установки требуется перезагрузка компьютера.|  
  
### <a name="handling-restarts"></a>Обработка перезапуска  
 При запуске установщика оболочки с помощью **/norestart** аргумент, указанный, он не перезагрузить компьютер или запрашивать необходимо перезагрузить компьютер. Тем не менее может потребоваться перезагрузка, и необходимо убедиться, что установщик продолжается после перезагрузки компьютера.  
  
 Для правильной обработки перезагрузки, убедитесь в том, что только одна программа установки — набор для возобновления и правильной обработки возобновить процесс.  
  
 Если возвращается ERROR_SUCCESS_REBOOT_REQUIRED или 3015 кода следует перезагрузить компьютер перед продолжением установки.  
  
 Для обработки перезапуска, выполните эти действия.  
  
-   Значение реестра, чтобы возобновить установку при запуске Windows.  
  
-   Выполните перезапуск двойные загрузчика.  
  
-   Удалите раздел ResumeData установщика оболочки.  
  
-   Перезагрузите Windows.  
  
-   Сброс начала путь к MSI-ФАЙЛ.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Параметр реестра, чтобы возобновить установку при запуске Windows  
 Раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ выполняется при запуске системы с правами администратора и затем стирается. HKEY_CURRENT_USER содержит аналогичные ключ, но он работает как обычный пользователь и не подходит для установки. Можно продолжить установку, помещая строковое значение в ключе однократного запуска, который вызывает установщик. Однако рекомендуется вызывать установщик, с помощью **/перезапустить** или аналогичный параметр, чтобы уведомить приложение, которое возобновляет работу вместо запуска. Можно также включить параметры, чтобы указать, где находятся в процесс установки, что особенно полезно в установках, которые может потребоваться несколько перезагрузок.  
  
 В следующем примере показано RunOnce раздела реестра для возобновления установки.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Установка двойные перезапуска загрузчика  
 При использовании установки непосредственно из RunOnce рабочего стола не сможет загрузить полностью. Для предоставления полного пользовательского интерфейса, необходимо создать другой выполнения программы установки и завершения однократного запуска экземпляра.  
  
 Программе установки необходимо выполнить повторно, чтобы он получает необходимые разрешения, и присвойте ему достаточно сведений, чтобы знать, где был остановлен перед перезагрузкой компьютера, как показано в следующем примере.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Идет удаление ключа ResumeData установщика оболочки  
 Установщик оболочки задает раздел реестра HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData с данными, чтобы возобновить выполнение программы установки после перезагрузки компьютера. Поскольку приложение не установщик оболочки, возобновление, удалите разделу реестра, как показано в следующем примере.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Перезапуск Windows  
 После выбора требуемые разделы реестра, можно перезапустить Windows. В следующем примере вызывается команды перезапуска для разных операционных систем Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Сброс путь запуска MSI-пакета  
 Перед перезагрузкой текущий каталог является расположение программы установки, но после перезапуска расположение становится каталог system32. Программа установки должна сбросить текущий каталог перед каждым вызовом MSI-ФАЙЛ, как показано в следующем примере.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Запуск приложения MSI  
 После установки оболочки Visual Studio возвращает ERROR_SUCCESS, можно запустить MSI-ФАЙЛ для приложения. Поскольку программа установки предоставляет пользовательский интерфейс, запустите MSI-ФАЙЛЕ в тихом режиме (**/q**) и с ведением журнала (**/L**), как показано в следующем примере.  
  
```cpp  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Создание базового приложения изолированной оболочки](walkthrough-creating-a-basic-isolated-shell-application.md)