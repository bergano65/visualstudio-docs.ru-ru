---
title: Пошаговое руководство. Создание из нескольких компьютеров создавать среду с | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4dff468ff42173e61c2f7006802c96a11120bd30
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769080"
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>Пошаговое руководство. Создание среды построения из нескольких компьютеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы развернуть среду построения в организации, необходимо установить Visual Studio на главный компьютер, а затем скопировать различные файлы и параметры на другой компьютер, который будет использоваться в процессе построения. Устанавливать Visual Studio на другой компьютер не нужно.  
  
 Этот документ не предоставляет прав на распространение программного обеспечение на стороне или предоставление сред построения третьим лицам.  
  
||  
|-|  
|Отказ от ответственности<br /><br /> Данный документ предоставляется "как есть". Мы протестировали приведенные далее шаги, но не имеем возможности провести полноценное тестирование всех возможных конфигураций. Мы приложим все усилия, чтобы своевременно обновлять этот документ по мере поступления дополнительной информации. Сведения и мнения, содержащиеся в данном документе, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления. Корпорация Майкрософт не дает никаких гарантий, явных или подразумеваемых, относительно предоставленной здесь информации. Вы принимаете на себя весь риск, связанный с его использованием.<br /><br /> Этот документ не предоставляет вам каких-либо юридических прав интеллектуальной собственности на какие-либо продукты Майкрософт. Вы можете копировать и использовать этот документ для внутренних справочных целей.<br /><br /> Вы не обязаны предоставлять Майкрософт какие-либо предложения, комментарии или отзывы ("Отзывы") в отношении этого документа. Тем не менее Майкрософт может использовать предоставляемые вами на добровольной основе Отзывы в своих продуктах, связанных спецификациях или другой документации (в совокупности "Предложения Майкрософт"), которые, в свою очередь, могут использоваться третьими лицами для разработки собственных продуктов. Соответственно, передавая Майкрософт Отзывы в отношении любой версии этого документа или Предложений Майкрософт, к которым они относятся, вы соглашаетесь, что : (а) Майкрософт вправе свободно использовать, воспроизводить, лицензировать, распространять и иным образом использовать для получения выгоды ваши Отзывы в любых Предложениях Майкрософт; (б) вы также безвозмездно предоставляете третьим лицам только те патентные права, которые необходимы для использования другими продуктами любых частей Продуктов Майкрософт, содержащих ваши Отзывы, и взаимодействия с ними; и (в) вы не предоставляете Майкрософт какие-либо Отзывы, которые (i) по вашему обоснованному мнению могут быть защищены заявками или правами на патентные, авторские или любые другие права интеллектуальной собственности любых третьих лиц; или (ii) регламентируются условиями лицензии, которые требуют лицензировать или иным образом передать любому третьему лицу Предложение Майкрософт, содержащее такие Отзывы или созданные на их основе.|  
  
 Это пошаговое руководство было протестировано для следующих операционных систем с помощью средства MSBuild в командной строке и Team Foundation Build.  
  
- Windows 8 (x86 и x64)  
  
- Windows 7 Максимальная  
  
- Windows Server 2008 R2 Standard  
  
  После выполнения этого пошагового руководства вы сможете использовать среду с несколькими компьютерами для построения приложений следующих видов:  
  
- Классические приложения C++, использующие пакет SDK для Windows 8  
  
- Классические приложения Visual Basic или C# для платформы .NET Framework 4.5  
  
  Среду с несколькими компьютерами нельзя использовать для построения приложений следующих видов:  
  
- Приложения [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Для построения приложений [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] необходимо установить Visual Studio на компьютер построения.  
  
- Классические приложения для платформы .NET Framework 4 или более ранней версии. Для построения таких приложений необходимо установить Visual Studio или ссылочные сборки и средства .NET (из пакета SDK для Windows 7.1) на компьютер построения.  
  
  Это пошаговое руководство состоит из следующих разделов:  
  
- [Установка программного обеспечения на компьютеры](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
- [Копирование файлов с главного компьютера на компьютер построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
- [Создание параметров реестра](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
- [Задание переменных среды для компьютера построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
- [Установка сборок MSBuild в глобальный кэш сборок (GAC) на компьютере построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
- [Сборка проектов](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
- [Создание среды построения с возможностью возврата в систему управления версиями](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Лицензированная копия Visual Studio Ultimate, Visual Studio Premium или Visual Studio Professional.  
  
-   Копия .NET Framework 4.5.1, которую можно скачать с веб-сайта [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software).  
  
##  <a name="InstallingSoftware"></a> Установка программного обеспечения на компьютеры  
 Сначала необходимо настроить главный компьютер, а затем компьютер построения.  
  
 При установке Visual Studio на главный компьютер создаются файлы и параметры, которые впоследствии необходимо скопировать на компьютер построения. Visual Studio можно установить на компьютер с архитектурой x86 или x64, но при этом главный компьютер и компьютер построения должны иметь одинаковые архитектуры.  
  
#### <a name="to-install-software-on-the-computers"></a>Установка программного обеспечения на компьютеры  
  
1.  Установите Visual Studio на главный компьютер.  
  
2.  Установите .NET Framework 4.5 на компьютер построения. Чтобы проверить правильность установки, убедитесь, что значение в разделе реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full@Version начинается с "4.5".  
  
##  <a name="CopyingFiles"></a> Копирование файлов с главного компьютера на компьютер построения  
 В этом разделе описывается копирование необходимых файлов, компиляторов, средств построения, ресурсов MSBuild и параметров реестра с главного компьютера на компьютер построения. При разработке этих инструкций подразумевалось, что решение Visual Studio установлено на главном компьютере в каталоге по умолчанию. Если установка выполнена в другом месте, внесите соответствующие изменения.  
  
- На компьютере с архитектурой x86 установка по умолчанию производится в папку C:\Program Files\Microsoft Visual Studio 11.0\  
  
- На компьютере с архитектурой x64 установка по умолчанию производится в папку C:\Program Files (x86)\Microsoft Visual Studio 11.0\  
  
  Обратите внимание, что имя папки Program Files зависит от установленной операционной системы. На компьютере с архитектурой x86 она называется \Program Files\\. На компьютере с архитектурой x64 эта папка называется \Program Files (x86)\\. Независимо от архитектуры системы в этом пошаговом руководстве папка Program Files называется %ProgramFiles%.  
  
> [!NOTE]
>  На компьютере построения все соответствующие файлы должны находиться на том же диске. При этом буква диска может отличаться от буквы диска на главном компьютере, на котором находится Visual Studio. В любом случае необходимо учитывать расположение файлов при создании записей реестра, как описано далее в этом документе.  
  
#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Копирования файлов пакета SDK для Windows на компьютер построения  
  
1. Если у вас установлен только пакет SDK для Windows 8, рекурсивно скопируйте эти папки с главного компьютера на компьютер построения:  
  
   - %ProgramFiles%\Windows Kits\8.0\bin\  
  
   - %ProgramFiles%\Windows Kits\8.0\Catalogs\  
  
   - %ProgramFiles%\Windows Kits\8.0\DesignTime\  
  
   - %ProgramFiles%\Windows Kits\8.0\include\  
  
   - %ProgramFiles%\Windows Kits\8.0\Lib\  
  
   - %ProgramFiles%\Windows Kits\8.0\Redist\  
  
   - %ProgramFiles%\Windows Kits\8.0\References\  
  
     Если у вас также установлены другие комплекты для Windows 8...  
  
   - Комплект средств для развертывания и оценки Microsoft Windows  
  
   - Комплект разработки драйверов для Microsoft Windows  
  
   - Комплект сертификации оборудования для Microsoft Windows  
  
     ...в папках %ProgramFiles%\Windows Kits\8.0\ могут присутствовать установленные файлы, которые перечислены на предыдущем шаге, причем их условиями лицензирования могут быть запрещены права на использование этих файлов на сервере построения. Проверьте условия лицензионного соглашения для каждого установленного комплекта для Windows и убедитесь, что соответствующие файлы можно копировать на компьютер построения. Если условия лицензии не разрешают использовать их на сервере построения, удалите эти файлы с компьютера построения.  
  
2. Скопируйте рекурсивно следующие папки с главного компьютера на компьютер построения:  
  
   -   %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\  
  
   -   %ProgramFiles%\Common Files\Merge Modules\  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\VC\  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\ProjectComponents\  
  
   -   %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\  
  
   -   %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\  
  
   -   %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\  
  
3. Скопируйте следующие файлы с главного компьютера на компьютер построения:  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msobj110.dll  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdb110.dll  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbcore.dll  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbsrv.exe  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msvcdis110.dll  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\makehm.exe  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat  
  
   -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat  
  
4. Следующие библиотеки среды выполнения Visual C++ необходимы только в том случае, если вы запускаете сборку на компьютере построения, например в рамках автоматизированного тестирования. Эти файлы, как правило, находятся во вложенных папках %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86\ или %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64\, в зависимости от архитектуры системы. В системах с архитектурой x86 скопируйте двоичные файлы x86 в папку \Windows\System32\. В системах x64 скопируйте двоичные файлы x86 в папку Windows\SysWOW64\, а двоичные файлы x64 в папку Windows\System32\.  
  
   -   \Microsoft.VC110.ATL\atl110.dll  
  
   -   \Microsoft.VC110.CRT\msvcp110.dll  
  
   -   \Microsoft.VC110.CRT\msvcr110.dll  
  
   -   \Microsoft.VC110.CXXAMP\vcamp110.dll  
  
   -   \Microsoft.VC110.MFC\mfc110.dll  
  
   -   \Microsoft.VC110.MFC\mfc110u.dll  
  
   -   \Microsoft.VC110.MFC\mfcm110.dll  
  
   -   \Microsoft.VC110.MFC\mfcm110u.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110chs.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110cht.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110deu.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110enu.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110esn.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110fra.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110ita.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110jpn.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110kor.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110rus.dll  
  
   -   \Microsoft.VC110.OPENMP\vcomp110.dll  
  
5. Скопируйте только следующие файлы из папки \Debug_NonRedist\x86\ или \Debug_NonRedist\x64\ на компьютере построения, как описывается в разделе [Подготовка тестового компьютера для запуска исполняемого файла отладки](http://msdn.microsoft.com/library/f0400989-cc2e-4dce-9788-6bdbe91c6f5a). Другие файлы не копируются.  
  
   -   \Microsoft.VC110.DebugCRT\msvcp110d.dll  
  
   -   \Microsoft.VC110.DebugCRT\msvcr110d.dll  
  
   -   \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfc110d.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfc110ud.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfcm110d.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfcm110ud.dll  
  
   -   \Microsoft.VC110.DebugOpenMP\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> Создание параметров реестра  
 Необходимо создать записи реестра для настройки параметров для MSBuild.  
  
#### <a name="to-create-registry-settings"></a>Создание параметров реестра  
  
1. Определите родительскую папку для записей реестра. Все записи реестра создаются в одном родительском разделе. На компьютере с архитектурой x86 родительским является раздел HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. На компьютере с архитектурой x64 родительским является раздел HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Независимо от архитектуры системы в этом пошаговом руководстве родительский раздел называется %RegistryRoot%.  
  
   > [!NOTE]
   >  Если архитектура главного компьютера отличается от компьютера построения, убедитесь, что используется соответствующий родительский раздел на каждом компьютере. Это особенно важно, если вы осуществляете автоматизацию процесса экспорта.  
   >   
   >  Кроме того, если на компьютере построения буква диска отличается от той, которая используется на главном компьютере, соответствующим образом измените значения записей реестра.  
  
2. Создайте следующие записи реестра на компьютере построения. Все эти записи представляют собой строки (Type == "REG_SZ" в реестре). Присвойте этим записям значения, аналогичные сопоставимым значениям на главном компьютере.  
  
   - %RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder  
  
   - %RegistryRoot%\VisualStudio\11.0@Source Directories  
  
   - %RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@11.0  
  
   - %RegistryRoot%\VisualStudio\SxS\VS7@11.0  
  
   - %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot  
  
   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath  
  
   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10  
  
   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11  
  
     На компьютере построения с архитектурой x64 также создайте следующую запись реестра, основываясь на соответствующих значениях на главном компьютере.  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder  
  
     Если компьютер построения имеет архитектуру x64 и вы хотите использовать 64-разрядную версию MSBuild, а также при использовании службы построения Team Foundation Server на компьютере x64, необходимо создать следующие записи реестра в собственном 64-разрядном реестре. При установке значений этих записей руководствуйтесь соответствующими значениями на главном компьютере.  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> Задание переменных среды для компьютера построения  
 Чтобы использовать MSBuild на компьютере построения, необходимо задать переменные среды PATH. Вы можете задать переменные с помощью файла vcvarsall.bat или настроить их вручную.  
  
#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Использование файла vcvarsall.bat для установки переменных среды  
  
-   Откройте окно командной строки на компьютере построения и запустите файл %Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat. С помощью аргумента командной строки укажите набор средств, который вы хотите использовать — x86, собственный x64 или кроссплатформенный компилятор x64. Если аргумент командной строки не указан, используется набор средств x86.  
  
     В этой таблице описываются поддерживаемые аргументы для файла vcvarsall.bat:  
  
    |Аргумент Vcvarsall.bat|Компилятор|Архитектура компьютера построения|Архитектура выходных данных сборки|  
    |----------------------------|--------------|---------------------------------|-------------------------------|  
    |x86 (по умолчанию)|Собственная 32-разрядная|x86, x64|x86|  
    |x86_amd64|Кроссплатформенный компилятор x64|x86, x64|X64|  
    |amd64|Собственная x64|X64|X64|  
  
     В случае успешного выполнения файла vcvarsall.bat и отсутствия сообщений об ошибках вы можете пропустить следующий шаг и перейти к разделу [Установка сборок MSBuild в глобальный кэш сборок (GAC) на компьютере построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) этого документа.  
  
#### <a name="to-manually-set-environment-variables"></a>Установка переменных среды вручную  
  
1. Чтобы вручную настроить среду командной строки, необходимо добавить следующий путь к переменной среды PATH:  
  
   -   %Program Files%\Microsoft Visual Studio 11.0\Common7\IDE  
  
2. При необходимости можно также добавить следующие пути в переменную PATH, чтобы упростить использование MSBuild для построения решений.  
  
    Если вы хотите использовать собственное 32-разрядное средство MSBuild, добавьте следующие пути к переменной PATH:  
  
   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools  
  
   - %windir%\Microsoft.NET\Framework\v4.0.30319  
  
     Если вы хотите использовать собственное 64-разрядное средство MSBuild, добавьте следующие пути к переменной PATH:  
  
   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64  
  
   - %windir%\Microsoft.NET\Framework64\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> Установка сборок MSBuild в глобальный кэш сборок (GAC) на компьютере построения  
 Для работы MSBuild на компьютере построения необходимо установить дополнительные сборки в глобальный кэш сборок.  
  
#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>Копирование сборок с главного компьютера и их установка на компьютере построения  
  
1.  Скопируйте рекурсивно следующие сборки с главного компьютера на компьютер построения. Они будут установлены в глобальный кэш сборок, поэтому место их расположения на компьютере построения не имеет значения.  
  
    -   %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  Чтобы установить сборки в глобальный кэш сборок, найдите gacutil.exe на компьютере построения, используйте программу gacutil.exe на компьютере построения. Как правило, соответствующий файл находится в папке %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\. Если вы не можете найти эту папку, повторите действия, описываемые в разделе [Копирование файлов с главного компьютера на компьютер построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) этого пошагового руководства.  
  
     Откройте окно командной строки с правами администратора и выполните следующую команду для каждого файла:  
  
     **gacutil -i \<file>**  
  
    > [!NOTE]
    >  Для полной установки сборки в глобальный кэш сборок может потребоваться перезагрузка.  
  
##  <a name="BuildingProjects"></a> Сборка проектов  
 Для построения проектов и решений [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] можно использовать средство Team Foundation Build или командную строку. Если вы используете Team Foundation Build, это средство вызывает исполняемый файл MSBuild, соответствующий архитектуре системы.  В командной строке можно использовать 32- и 64-разрядную версию MSBuild. Кроме того, можно выбрать версию архитектуры MSBuild, задав переменную среды PATH или напрямую вызвав исполняемый файл MSBuild, соответствующий архитектуре.  
  
 Чтобы использовать средство msbuild.exe в командной строке, выполните следующую команду, где вместо *solution.sln* следует указать имя вашего решения.  
  
 **msbuild** *solution.sln*  
  
 Дополнительные сведения об использовании средства MSBuild в командной строке см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Для построения проектов [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] необходимо использовать набор инструментов платформы "v110". Если вы не хотите изменять файлы проекта [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], можно задать набор инструментов платформы с помощью следующего аргумента командной строки:  
>   
>  **msbuild** *solution.sln* **/p:PlatformToolset=v110**  
  
##  <a name="CreatingForSourceControl"></a> Создание среды построения с возможностью возврата в систему управления версиями  
 Вы можете создать среду построения, которая может развертываться на различных компьютерах и не требует установки файлов в глобальный кэш сборок или изменения параметров реестра. Ниже приведен один из способов сделать это. Внесите в эту процедуру изменения в соответствии с характеристиками вашей среды построения.  
  
> [!NOTE]
>  Чтобы избежать ошибок tracker.exe во время построения, необходимо отключить добавочное построение. Чтобы отключить добавочное построение, задайте следующий параметр сборки:  
>   
>  **msbuild** *solution.sln* **/p:TrackFileAccess=false**  
  
#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>Создание среды построения с возможностью возврата в систему управления версиями  
  
1.  Создайте каталог "Depot" на главном компьютере.  
  
     В рамках этой процедуры этот каталог называется %Depot%.  
  
2.  Скопируйте каталоги и файлы, которые описываются в разделе [Копирование файлов с главного компьютера на компьютер построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) этого пошагового руководства, и вставьте их в созданный только что каталог %Depot%. Например, скопируйте файлы из каталога %ProgramFiles%\Windows Kits\8.0\bin\ в %Depot%\Windows Kits\8.0\bin\\.  
  
3.  После вставки файлов в каталог %Depot% внесите следующие изменения:  
  
    -   В файлах %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ и \Microsoft.CppCommon.targets\\ замените каждый экземпляр.  
  
         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
  
         в  
  
         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".  
  
         Первое имя относится к сборке, установленной в глобальный кэш сборок.  
  
    -   В файле %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets замените каждый экземпляр.  
  
         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
  
         в  
  
         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".  
  
4.  Создайте файл с расширением PROPS (например, Partner.AutoImports.props) и поместите его в корень папки, которая содержит ваши проекты. Этот файл служит для установки переменных, которые используются средством MSBuild для поиска различных ресурсов. Если переменные не заданы в этом файле, они устанавливаются в других файлах с расширением PROPS и TARGETS, в которых используются значения из реестра. Так как мы не устанавливаем значения реестра, эти переменные будут пустыми и построение завершится сбоем. Вместо этого необходимо добавить следующий код в файл Partner.AutoImports.props:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  Добавьте следующую строку в начало каждого файла проекта после строки `<Project Default Targets…>`.  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  Измените среду командной строки следующим образом:  
  
    -   Set Depot=*расположение каталога Depot, созданного на шаге 1*  
  
    -   Set path=%path%;*расположение MSBuild на компьютере*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 11.0\Common7\IDE\  
  
         Для собственной 64-разрядной архитектуры построения задайте ссылку на 64-разрядную версию MSBuild.  
  
## <a name="see-also"></a>См. также раздел  
 [Подготовка тестового компьютера для выполнения исполняемого файла отладки](http://msdn.microsoft.com/library/f0400989-cc2e-4dce-9788-6bdbe91c6f5a)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
