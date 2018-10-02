---
title: Установка приложений изолированной оболочки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7b1ba12f39accf863b051ec7096ee835a03ff64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563298"
---
# <a name="installing-an-isolated-shell-application"></a>Установка приложений изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Установка приложения Isolated Shell](https://docs.microsoft.com/visualstudio/extensibility/installing-an-isolated-shell-application).  
  
Чтобы установить приложение оболочки необходимо выполнить следующие действия.  
  
-   Подготовка решения.  
  
-   Создание пакета установщика Windows (MSI) для вашего приложения.  
  
-   Создайте начальный загрузчик программы установки.  
  
 Пример кода в этом документе берутся из [пример развертывания оболочки](http://go.microsoft.com/fwlink/?LinkId=262245), который можно загрузить из коллекции кода на веб-сайте MSDN. В этом примере результаты выполнения этих этапов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения процедур, которые в этом разделе описываются следующие средства должны устанавливаться на компьютере.  
  
-   Пакет SDK для Visual Studio  
  
-   [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) версии 3.6  
  
 Для примера также требуется Microsoft Visualization and Modeling SDK, где требуется не всем интерпретаторам команд.  
  
## <a name="preparing-your-solution"></a>Подготовка решения  
 По умолчанию шаблоны Shell сборки для пакетов VSIX, но это поведение предусмотрено в первую очередь для целей отладки. При развертывании приложения оболочки, необходимо использовать пакеты MSI, чтобы разрешить доступ к реестру и перезагрузка во время установки. Чтобы подготовить приложение для развертывания MSI, выполните следующие действия.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Чтобы подготовить приложение оболочки для развертывания MSI  
  
1.  Изменение каждого файла VSIXMANIFEST в решении.  
  
     В `Identifier` элемента, добавьте `InstalledByMSI` элемент и `SystemComponent` элемент и задайте их значения `true`.  
  
     Эти элементы не установщик VSIX пытался установить компоненты и пользователем из их удаления с помощью **расширения и обновления** диалоговое окно.  
  
2.  Для каждого проекта, который содержит манифест VSIX изменение задачи сборки для вывода содержимого в расположение, из которого будет устанавливать удостоверения MSI. Манифест VSIX включить в выходные данные сборки, но не создавайте VSIX-файл.  
  
## <a name="creating-an-msi-for-your-shell"></a>Создание MSI для Shell  
 Для создания пакета MSI, мы рекомендуем использовать [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) потому, что он предоставляет большую гибкость, чем стандартный проект установки.  
  
 В файле Product.wxs набор блоков обнаружения и макет компонентов оболочки.  
  
 Затем создайте записи реестра и в ApplicationRegistry.wxs REG-файл для вашего решения.  
  
### <a name="detection-blocks"></a>Обнаружение блоков  
 Обнаружение блок состоит из `Property` элемент, который задает необходимого компонента для обнаружения и `Condition` элемент, который задает сообщение для возврата, если необходимый компонент отсутствует на компьютере. Например приложение оболочки требует распространяемый пакет оболочки Microsoft Visual Studio и блок обнаружения будет напоминать следующую разметку.  
  
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
  
### <a name="layout-of-shell-components"></a>Макет оболочки компонентов  
 Необходимо добавить элементы для определения целевого структуру каталогов и компоненты для установки.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Чтобы задать макет оболочки компонентов  
  
1.  Создать иерархию `Directory` элементов, представляющих все каталоги, которые необходимо создать в файловой системе на целевом компьютере, как показано в следующем примере.  
  
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
  
     Эти каталоги, обозначенные `Id` когда указаны файлы, которые должны быть установлены.  
  
2.  Определение компонентов, необходимых для оболочка и приложение оболочки, как показано в следующем примере.  
  
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
  
    1.  `ComponentRef` Элемент ссылается на другой WXS-файл, определяющий файлы, которые требуется текущего компонента. Например GeneralProfile имеет следующее определение в HelpAbout.wxs.  
  
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
  
         `DirectoryRef` Элемент указывает, куда эти файлы на компьютере пользователя. `Directory` Элемент указывает, что он будет установлен в подкаталог, а для каждого `File` элемент представляет файл, введенное или существует как часть решения и определяет, где этот файл можно получить при создании MSI-файл.  
  
    2.  `ComponentGroupRef` Элемент ссылается на группу других компонентов (или компоненты и группы компонентов). Например `ComponentGroupRef` в ApplicationGroup определяется следующим образом в Application.wxs.  
  
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
    >  Необходимые зависимости для приложений, оболочка (изолированная): DebuggerProxy MasterPkgDef, ресурсы (особенно .winprf-файл), приложения и PkgDefs.  
  
### <a name="registry-entries"></a>Записи реестра  
 Шаблон проекта оболочка (изолированная) включает в себя *имя_проекта*REG-файл для разделов реестра для слияния при установке. Эти записи реестра должны быть частью MSI-ФАЙЛ для установки и очистки в целях. Также необходимо создать соответствующие блоки реестра в ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Чтобы интегрировать записи реестра в MSI-ФАЙЛ  
  
1.  В **настроек оболочки** откройте *имя_проекта*. reg.  
  
2.  Замените все вхождения маркер $ $RootFolder путь к каталогу установки целевой объект.  
  
3.  Добавьте другие записи реестра, которые требуются приложению.  
  
4.  Откройте ApplicationRegistry.wxs.  
  
5.  Для каждой записи реестра в *имя_проекта*файл с расширением REG, добавьте соответствующий блок реестра, как в приведенных ниже примерах.  
  
    |*Имя_проекта*файл с расширением REG|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= «Объект PhotoStudio DTE»|\<RegistryKey Id = «DteClsidRegKey» корневой = «HKCR» ключ = "$(var. DteClsidRegKey) "Action = «createAndRemoveOnUninstall» ><br /><br /> \<Тип RegistryValue = 'строка' имя = "@" значение = "$(var. Объект ShortProductName) DTE "/ ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= «$RootFolder$\PhotoStudio.exe»|\<RegistryKey Id = «DteLocSrv32RegKey» корневой = «HKCR» ключ = "$(var. \LocalServer32 DteClsidRegKey) "Action = «createAndRemoveOnUninstall» ><br /><br /> \<Тип RegistryValue = 'строка' имя = "@" значение = "[INSTALLDIR] $(var. ShortProductName) .exe "/ ><br /><br /> \</ RegistryKey >|  
  
     В этом примере Var.DteClsidRegKey разрешается в раздел реестра, в верхней строке. Разрешается Var.ShortProductName `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Создание загрузчика программы установки  
 Завершенные удостоверения MSI будет устанавливать только в том случае, если сначала установить все необходимые компоненты. Чтобы облегчить взаимодействие с пользователем, создайте программу установки, которая собирает и устанавливает все необходимые компоненты перед установкой приложения. Чтобы обеспечить успешную установку, выполните эти действия.  
  
-   Принудительной установки администратором.  
  
-   Определить, установлена ли оболочка Visual Studio (изолированная).  
  
-   Выполнение одного или обоих установщиков оболочки в порядке.  
  
-   Обрабатывать запросы перезапуска.  
  
-   Запустите удостоверения MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Применение установки администратором  
 Эта процедура необходима для включения в программу установки для доступа к обязательным каталогов, например \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Для принудительной установки администратором  
  
1.  Откройте контекстное меню для проекта установки, а затем выберите **свойства**.  
  
2.  В разделе **файл конфигурации свойства/компоновщика/Manifest**, задайте **уровень выполнения UAC** для **requireAdministrator**.  
  
     Это свойство устанавливает атрибут, который требуется программа для запуска от имени администратора в файле внедренного манифеста.  
  
### <a name="detecting-shell-installations"></a>Обнаружение установок оболочки  
 Чтобы определить, необходимо ли устанавливать Visual Studio Shell (изолированная), сначала определите, ли он установлен, проверив значение реестра HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Также эти значения считываются в блоке обнаружения оболочки в Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder указывает расположение, где была установлена оболочка Visual Studio, а вы можете проверить наличие файлов существует.  
  
 Пример того, как процедура обнаружения установки оболочки, см. в разделе `GetProductDirFromReg` функции Utilities.cpp в примере развертывания оболочки.  
  
 Если один или оба из Visual Studio оболочек, требующий пакет не установлен на компьютере, необходимо добавить их в список устанавливаемых компонентов. Например, см. в разделе `ComponentsPage::OnInitDialog` функции ComponentsPage.cpp в примере развертывания оболочки.  
  
### <a name="running-the-shell-installers"></a>Запуск оболочки установщиков  
 Чтобы запустить установщики оболочки, вызовите распространяемые компоненты оболочки Visual Studio, используя правильные аргументы командной строки. Как минимум, необходимо использовать аргументы командной строки **/q/norestart** и следить за код возврата определить, какие действия должны выполняться рядом. В следующем примере выполняется распространяемый пакет оболочки (изолированная).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Под управлением установщики оболочки языковой пакет  
 Если вместо этого обнаружится, что были установлены оболочки или оболочки, и просто требуется языковой пакет, можно установить языковые пакеты, как показано в следующем примере.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Знакомство с протоколами возвращаемые значения  
 В некоторых операционных системах установки Visual Studio Shell (изолированная), может потребоваться перезагрузка. Это условие можно определить с помощью код возврата вызова `ExecCmd`.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|ERROR_SUCCESS|Установка завершена. Теперь можно установить приложение.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Установка завершена. Приложения можно установить после перезагрузки компьютера.|  
|3015|Выполняется установка. Для продолжения установки требуется перезагрузка компьютера.|  
  
### <a name="handling-restarts"></a>Обработка перезапуска  
 При запуске установщика оболочки с помощью **/norestart** аргумент, вы указали, он не перезагрузить компьютер или обратиться за перезагрузки компьютера. Тем не менее может потребоваться перезагрузка, и необходимо убедиться, что установщик продолжается после перезагрузки компьютера.  
  
 Для правильной обработки перезагрузки, убедитесь, что только один программу установки, чтобы возобновить а правильную обработку процесс возобновления.  
  
 Если возвращается ошибка ERROR_SUCCESS_REBOOT_REQUIRED или 3015 кода необходимо перезапустить компьютер перед продолжением установки.  
  
 Для обработки перезагрузки, выполните следующие действия:  
  
-   Значение реестра, чтобы возобновить установку при запуске Windows.  
  
-   Выполните перезапуск double загрузчика.  
  
-   Удалите раздел ResumeData установщика оболочки.  
  
-   Перезагрузите Windows.  
  
-   Сброс начала путь к MSI-ФАЙЛ.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Параметр реестра, чтобы продолжить установку при запуске Windows  
 Раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ выполняет при запуске системы с правами администратора и затем удаляется. HKEY_CURRENT_USER содержит аналогичные ключ, но он работает как обычный пользователь и не подходит для установок. Можно продолжить установку, добавив в раздел RunOnce, который вызывает установщик значение строки. Тем не менее, мы рекомендуем вызывать установщик с помощью **/restart** или аналогичный параметр для уведомления, он возобновляет работу вместо запуска приложения. Также можно включить параметры, чтобы указать, где вы находитесь в процесс установки, что особенно полезно в установках, которые могут потребовать несколько перезапусков.  
  
 Пример значения ключа реестра RunOnce для возобновления установки.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Установка Double перезапуска загрузчика  
 Если программа установки используется непосредственно из RunOnce, рабочий стол будет невозможно загрузится полностью. Чтобы сделать доступным полный пользовательский интерфейс, необходимо создать другое выполнение программы установки и завершить экземпляр однократного запуска.  
  
 Программу установки необходимо выполнить повторно, чтобы он получает правильные разрешения, и присвойте ему достаточно информации, чтобы знать, где вы ранее остановились перезапуска, как показано в следующем примере.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Удаление ключа ResumeData установщика оболочки  
 Установщик оболочки задает раздел реестра HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData с данными, чтобы возобновить выполнение программы установки после перезагрузки. Поскольку приложения, не установщик оболочки, возобновляется, удалите такой раздел реестра, как показано в следующем примере.  
  
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
 Перед перезапуском текущий каталог является расположение программы установки, но, после перезагрузки, расположение становится каталог system32. Программе установки необходимо сбросить текущего каталога перед каждым вызовом MSI, как показано в следующем примере.  
  
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
 После установки оболочки Visual Studio значение ERROR_SUCCESS, можно запустить MSI-ФАЙЛ для приложения. Так как программа установки предоставляет пользовательский интерфейс, запустить удостоверения MSI в тихом режиме (**/q**) и с ведением журнала (**/L**), как показано в следующем примере.  
  
```cpp#  
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
 [Пошаговое руководство. Создание базового приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

