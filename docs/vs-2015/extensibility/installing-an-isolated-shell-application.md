---
title: Установка изолированного приложения оболочки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a077173a0d095ee10cc1fa16da3db1f3744dafa8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301156"
---
# <a name="installing-an-isolated-shell-application"></a>Установка приложений изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы установить приложение оболочки, необходимо выполнить следующие действия.  
  
- Подготовьте решение.  
  
- Создайте пакет установщик Windows (MSI) для приложения.  
  
- Создайте начальный загрузчик программы установки.  
  
  Весь пример кода в этом документе взят из [примера развертывания оболочки](https://go.microsoft.com/fwlink/?LinkId=262245), который можно скачать из коллекции кода на веб-сайте MSDN. В этом примере показаны результаты выполнения каждого из этих действий.  
  
## <a name="prerequisites"></a>Prerequisites  
 Для выполнения процедур, описанных в этом разделе, на компьютере должны быть установлены следующие средства.  
  
- Пакет SDK для Visual Studio  
  
- [Набор инструментов УСТАНОВЩИК Windows XML](https://go.microsoft.com/fwlink/?LinkId=82720) версии 3,6  
  
  Для примера также требуется пакет SDK для визуализации и моделирования Microsoft, который не все оболочки требуется.  
  
## <a name="preparing-your-solution"></a>Подготовка решения  
 По умолчанию шаблоны оболочки создают пакеты VSIX, но это поведение предназначено главным образом для целей отладки. При развертывании приложения оболочки необходимо использовать пакеты MSI, чтобы обеспечить доступ к реестру и перезагрузку во время установки. Чтобы подготовить приложение к развертыванию MSI, выполните следующие действия.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Подготовка приложения оболочки для развертывания MSI  
  
1. Измените каждый файл. vsixmanifest в решении.  
  
     В элементе `Identifier` добавьте элемент `InstalledByMSI` и элемент `SystemComponent`, а затем задайте для них значение `true`.  
  
     Эти элементы не позволяют установщику VSIX пытаться установить компоненты, а пользователь не сможет их удалить с помощью диалогового окна **расширения и обновления** .  
  
2. Для каждого проекта, содержащего манифест VSIX, измените задачи сборки, чтобы вывести содержимое в расположение, из которого будет устанавливаться MSI. Включите манифест VSIX в выходные данные сборки, но не создавайте VSIX-файл.  
  
## <a name="creating-an-msi-for-your-shell"></a>Создание MSI для оболочки  
 Для создания пакета MSI рекомендуется использовать [набор инструментов УСТАНОВЩИК Windows XML](https://go.microsoft.com/fwlink/?LinkId=82720) , так как он обеспечивает большую гибкость, чем стандартный проект установки.  
  
 В файле Product. WXS задайте блоки обнаружения и макет компонентов оболочки.  
  
 Затем создайте записи реестра в файле с расширением REG для решения и в Аппликатионрегистри. WXS.  
  
### <a name="detection-blocks"></a>Блоки обнаружения  
 Блок обнаружения состоит из элемента `Property`, который указывает необходимое условие для обнаружения, и элемент `Condition`, указывающий возвращаемое сообщение, если необходимый компонент отсутствует на компьютере. Например, для приложения оболочки потребуется распространяемый компонент оболочки Microsoft Visual Studio, а блок обнаружения будет выглядеть так, как показано в следующей разметке.  
  
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
 Необходимо добавить элементы для определения целевой структуры каталогов и устанавливаемых компонентов.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Настройка макета компонентов оболочки  
  
1. Создайте иерархию элементов `Directory` для представления всех каталогов, создаваемых в файловой системе на конечном компьютере, как показано в следующем примере.  
  
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
  
     На эти каталоги ссылаются `Id` при указании файлов, которые должны быть установлены.  
  
2. Найдите компоненты, необходимые оболочке и приложению оболочки, как показано в следующем примере.  
  
    > [!NOTE]
    > Некоторые элементы могут ссылаться на определения в других файлах WXS.  
  
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
  
    1. Элемент `ComponentRef` ссылается на другой файл WXS, который определяет файлы, необходимые для текущего компонента. Например, Женералпрофиле имеет следующее определение в Хелпабаут. WXS.  
  
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
  
         Элемент `DirectoryRef` указывает, где находятся эти файлы на компьютере пользователя. Элемент `Directory` указывает, что он будет установлен во вложенный каталог, а каждый элемент `File` представляет файл, который создан или существует как часть решения, и определяет, где можно найти этот файл при создании MSI-файла.  
  
    2. Элемент `ComponentGroupRef` ссылается на группу других компонентов (или компонентов и групп компонентов). Например, `ComponentGroupRef` в разделе ApplicationGroup определяется следующим образом в Application. WXS.  
  
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
    > Необходимые зависимости для приложений оболочки (изолированной): DebuggerProxy, Мастерпкгдеф, Resources (особенно файл. винпрф), Application и Пкгдефс.  
  
### <a name="registry-entries"></a>Записи реестра  
 Шаблон проекта Shell (изолированная среда) включает файл *имяПроекта*. reg для разделов реестра, которые необходимо объединить при установке. Эти записи реестра должны быть частью MSI в целях установки и очистки. Кроме того, необходимо создать соответствующие блоки реестра в Аппликатионрегистри. WXS.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Интеграция записей реестра в MSI  
  
1. В папке **Настройка оболочки** откройте *имя_проекта*. reg.  
  
2. Замените все экземпляры токена $RootFolder $ на путь к целевому каталогу установки.  
  
3. Добавьте любые другие записи реестра, необходимые приложению.  
  
4. Откройте Аппликатионрегистри. WXS.  
  
5. Для каждой записи реестра в *ProjectName*. reg добавьте соответствующий блок реестра, как показано в следующих примерах.  
  
    |*Имя_проекта*. reg|Аппликатионрегисти. WXS|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT \КЛСИД\\{bb431796-A179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "Объект в студии DTE"|\<RegistryKey ID = ' Дтеклсидрегкэй ' root = ' HKCR ' key = ' $ (var. Дтеклсидрегкэй) "Action =" Креатеандремовеонунинсталл "><br /><br /> \<RegistryValue Type = "String" name = ' @ ' value = ' $ (var. Шортпродуктнаме) объект DTE "/><br /><br /> \</Регистрикэй >|  
    |[HKEY_CLASSES_ROOT \КЛСИД\\{bb431796-A179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey ID = ' DteLocSrv32RegKey ' root = ' HKCR ' key = ' $ (var. Дтеклсидрегкэй) \LocalServer32 "Action =" Креатеандремовеонунинсталл "><br /><br /> \<RegistryValue Type = "String" name = ' @ ' value = ' [INSTALLDIR] $ (var. Шортпродуктнаме). exe '/><br /><br /> \</Регистрикэй >|  
  
     В этом примере var. Дтеклсидрегкэй разрешается в раздел реестра в верхней строке. Var. Шортпродуктнаме разрешается в `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Создание начального загрузчика программы установки  
 Завершенный MSI будет установлен только в том случае, если все необходимые компоненты установлены первыми. Чтобы упростить работу с конечным пользователем, создайте программу установки, которая собирает и устанавливает все необходимые компоненты перед установкой приложения. Чтобы обеспечить успешную установку, выполните следующие действия.  
  
- Принудительная установка с помощью администратора.  
  
- Определить, установлена ли оболочка Visual Studio (изолированная).  
  
- Запустите один или оба установщика оболочки по порядку.  
  
- Обрабатывает запросы на перезагрузку.  
  
- Запустите MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Принудительная установка администратором  
 Эта процедура необходима для предоставления программе установки доступа к необходимым каталогам, таким как \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Принудительная установка администратором  
  
1. Откройте контекстное меню проекта установки и выберите пункт **Свойства**.  
  
2. В разделе **Свойства конфигурации/компоновщик/файл манифеста**задайте для параметра **уровень выполнения UAC** значение **requireAdministrator**.  
  
     Это свойство помещает атрибут, требующий запуска программы от имени администратора во внедренном файле манифеста.  
  
### <a name="detecting-shell-installations"></a>Обнаружение установок оболочки  
 Чтобы определить, должна ли быть установлена оболочка Visual Studio (изолированная), сначала определите, установлена ли она, путем проверки значения реестра Хклм\софтваре\микрософт\девдив\вс\сервиЦинг\шеллверсион\исошелл\лЦид\инсталл.  
  
> [!NOTE]
> Эти значения также считываются блоком обнаружения оболочки в Product. WXS.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder указывает расположение, в котором установлена оболочка Visual Studio, и можно проверить наличие файлов.  
  
 Пример обнаружения установки оболочки см. в описании функции `GetProductDirFromReg` Utilities. cpp в примере развертывания оболочки.  
  
 Если одна или обе оболочки Visual Studio, необходимые для пакета, не установлены на компьютере, необходимо добавить их в список компонентов для установки. Пример см. в описании функции `ComponentsPage::OnInitDialog` Компонентспаже. cpp в примере развертывания оболочки.  
  
### <a name="running-the-shell-installers"></a>Запуск установщиков оболочки  
 Чтобы запустить установщики оболочки, вызовите распространяемые оболочки Visual Studio с помощью правильных аргументов командной строки. Как минимум, необходимо использовать аргументы командной строки **/norestart/q** и Watch для кода возврата, чтобы определить, что следует делать далее. Следующий пример запускает распространяемый компонент оболочки (изолированной).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Запуск установщиков языкового пакета оболочки  
 Если вместо этого вы обнаружите, что оболочка или оболочки установлены и требуется только языковой пакет, можно установить языковые пакеты, как показано в следующем примере.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Расшифровка возвращаемых значений  
 В некоторых операционных системах для установки оболочки Visual Studio (изолированной) потребуется перезагрузка. Это условие можно определить с помощью кода возврата вызова `ExecCmd`.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|ERROR_SUCCESS|Установка завершена. Теперь можно установить приложение.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Установка завершена. Приложение можно установить после перезагрузки компьютера.|  
|3015|Выполняется установка. Для продолжения установки требуется перезагрузка компьютера.|  
  
### <a name="handling-restarts"></a>Обработка перезапусков  
 При запуске установщика оболочки с помощью аргумента **/norestart** вы указали, что он не перезагружает компьютер или не запрашивает перезагрузку компьютера. Однако может потребоваться перезагрузка, и необходимо убедиться, что установщик продолжит работу после перезагрузки компьютера.  
  
 Для правильной обработки перезапусков убедитесь, что для одной программы установки задано возобновление и что процесс возобновления будет обрабатываться правильно.  
  
 Если возвращается значение ERROR_SUCCESS_REBOOT_REQUIRED или 3015, код должен перезагрузить компьютер перед продолжением установки.  
  
 Для выполнения перезапусков выполните следующие действия.  
  
- Настройка реестра для возобновления установки при запуске Windows.  
  
- Выполните двойной перезапуск начального загрузчика.  
  
- Удалите ключ Ресумедата установщика оболочки.  
  
- Перезапустите Windows.  
  
- Сброс начального пути MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Настройка реестра для возобновления установки при запуске Windows  
 Раздел реестра HKEY_LOCAL_MACHINE \Софтваре\микрософт\виндовс\куррентверсион\рунонце\ выполняется при запуске системы с правами администратора, а затем удаляется. HKEY_CURRENT_USER содержит аналогичный ключ, но он работает от имени обычного пользователя и не подходит для установки. Можно возобновить установку, поместив строковое значение в раздел RunOnce, который вызывает установщик. Однако рекомендуется вызывать установщик с помощью **/restart** или аналогичного параметра, чтобы уведомить приложение о том, что оно возобновляется вместо запуска. Можно также включить параметры, чтобы указать, где находится процесс установки, что особенно полезно в установках, для которых может потребоваться несколько перезагрузок.  
  
 В следующем примере показано значение раздела реестра RunOnce для возобновления установки.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Установка двойного перезапуска начального загрузчика  
 Если программа установки используется непосредственно из RunOnce, Рабочий стол не сможет полностью загрузиться. Чтобы сделать доступным полный пользовательский интерфейс, необходимо создать еще одно выполнение программы установки и завершить экземпляр RunOnce.  
  
 Необходимо повторно запустить программу установки, чтобы она получала правильные разрешения, и необходимо предоставить достаточно информации, чтобы узнать, где вы остановились перед перезапуском, как показано в следующем примере.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Удаление ключа Ресумедата установщика оболочки  
 Установщик оболочки устанавливает раздел реестра HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData с данными, чтобы возобновить установку после перезагрузки. Так как приложение, а не установщик оболочки, возобновляет работу, удалите этот раздел реестра, как показано в следующем примере.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Перезапуск Windows  
 После настройки необходимых разделов реестра можно перезапустить Windows. В следующем примере вызываются команды перезапуска для различных операционных систем Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Сброс начального пути MSI  
 Перед перезагрузкой текущим каталогом является расположение программы установки, но после перезагрузки расположение становится каталогом System32. Программа установки должна сбрасывать текущий каталог перед вызовом MSI, как показано в следующем примере.  
  
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
  
### <a name="running-the-application-msi"></a>Запуск MSI приложения  
 После того как установщик оболочки Visual Studio возвратит ERROR_SUCCESS, можно запустить MSI для приложения. Так как программа установки предоставляет пользовательский интерфейс, запустите MSI в тихом режиме ( **/q**) и с ведением журнала ( **/l**), как показано в следующем примере.  
  
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
