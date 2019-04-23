---
title: Параметры командной строки для команды Devenv | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4eadb8c9553873f43ad9435ad43fae00f57affcb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050716"
---
# <a name="devenv-command-line-switches"></a>Параметры командной строки для команды Devenv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Команда Devenv позволяет задавать из командной строки различные параметры для интегрированной среды разработки (IDE), а также для сборки, отладки и развертывания проектов. Используйте эти параметры для запуска IDE из файла скрипта или из BAT-файла, например скрипта сборки программы в ночное время, либо для запуска IDE в особой конфигурации.  
  
> [!NOTE]
>  Для задач, связанных со сборкой, теперь рекомендуется использовать MSBuild вместо devenv. Дополнительные сведения см. в [справочнике по командной строке](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Для использования параметров [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) и [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) нужно запустить devenv от имени администратора.  
  
## <a name="devenv-switch-syntax"></a>Синтаксис параметров команды Devenv  
 По умолчанию команды devenv передают параметры в служебную программу devenv.com.  
  
 Использование devenv.com обеспечивает доставку выходных данных с помощью стандартных системных потоков, таких как `stdout` и `stderr`, а также правильную переадресацию ввода-вывода при записи выходных данных, например в TXT-файл. Для команд, начинающихся с `devenv.exe`, можно использовать те же параметры, но они будут отправляться в программу devenv.exe в обход служебной программы devenv.com.  
  
 Правила синтаксиса для параметров `devenv` похожи на правила для других служебных программ командной строки DOS. Приведенные ниже правила синтаксиса действуют для всех параметров `devenv` и их аргументов.  
  
- Команды начинаются с `devenv`.  
  
- Регистр в параметрах не учитывается.  
  
- При указании решения или проекта первым аргументом будет имя файла решения или файла проекта, включающее путь к файлу.  
  
- Если первый аргумент — это файл, который не является решением или проектом, то этот файл откроется в соответствующем редакторе в новом экземпляре IDE.  
  
- Если вместо имени файла решения указать имя файла проекта, команда `devenv` выполнит поиск файла решения с этим именем в родительской папке файла проекта. Например, команда `devenv /build myproject1.vbproj` выполнит поиск файла решения с именем myproject1.sln в родительской папке.  
  
    > [!NOTE]
    >  В этой родительской папке должен находиться только один файл решения, ссылающийся на проект. Если в родительской папке отсутствует файл решения, который ссылается на проект, или если в ней два или более файлов решения, ссылающихся на проект, то будет создан временный файл решения с именем этого проекта и ссылками на него.  
  
- Пути к файлам и имена файлов, содержащие пробелы, должны заключаться в двойные кавычки (""). Например, "c:\project a\\".  
  
- Разделяйте параметры и аргументы в одной строке одиночными пробелами. Например, команда **devenv /log output.txt** открывает среду IDE и выводит все данные журнала для данного сеанса в файл output.txt.  
  
- В командах `devenv` нельзя использовать синтаксис сопоставления шаблонов.  
  
## <a name="devenv-switches"></a>Параметры команды Devenv  
 Используйте перечисленные ниже параметры командной строки для отображения интегрированной среды разработки и выполнения описанных задач.  
  
|Параметр командной строки|Описание|  
|-------------------------|-----------------|  
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Запускает среду IDE и выполняет указанную команду.|  
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Загружает исполняемый файл [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] под управлением отладчика. Этот параметр недоступен для исполняемых файлов [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] и [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Дополнительные сведения см. в разделе [Автоматический запуск процесса в отладчике](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) или `/l`|Задает язык по умолчанию для среды IDE. Если указанный язык не включен в установку Visual Studio, то этот параметр будет игнорироваться.|  
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Запускает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и записывает все действия в файл журнала.|  
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) или `/r`|Компилирует и запускает указанное решение.|  
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Компилирует и выполняет указанное решение, свертывая окно IDE при выполнении решения и закрывая IDE после завершения выполнения.|  
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Инициирует использование в IDE переменных среды PATH, INCLUDE и LIB для компиляции на [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] вместо параметров, указанных в диалоговом окне **Параметры** в разделе "Каталоги VC++" параметров **проектов**. Дополнительные сведения см. в разделе [Установка переменных пути и среды при построении из командной строки](http://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4).|  
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Открывает указанные файлы в запущенном экземпляре этого приложения. Если нет запущенных экземпляров, то запускается новый экземпляр с упрощенной структурой окна.|  
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Запускает экземпляр среды IDE Visual Studio без загрузки указанной надстройки.|  
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Запускает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в безопасном режиме и загружает только среду и службы по умолчанию, а также прилагаемые версии сторонних пакетов.|  
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Удаляет все теги SkipLoading, добавленные в пакеты VSPackage пользователями, желающими исключить загрузку проблемных пакетов VSPackage.|  
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Заставляет Visual Studio выполнить слияние метаданных ресурсов, описывающих меню, панели инструментов и группы команд, из всех доступных пакетов VSPackage.|  
  
 Используйте перечисленные ниже параметры командной строки для выполнения описанных задач. Эти параметры командной строки не отображают интегрированную среду разработки.  
  
|Параметр командной строки|Описание|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Отображает справку по параметрам devenv в **окне командной строки**.<br /><br /> **Devenv /?**|  
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Выполняет сборку указанного решения или проекта согласно конфигурации заданного решения.<br /><br /> **Devenv myproj.csproj /build**|  
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Удаляет все файлы, созданные командой сборки, не затрагивая исходные файлы.<br /><br /> **Devenv myproj.csproj /clean**|  
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Выполняет сборку решения, а также файлов, необходимых для развертывания, согласно конфигурации решений.<br /><br /> **Devenv myproj.csproj /deploy**|  
|[/Diff](../../ide/reference/diff.md)|Сравнение двух файлов.  Принимает четыре параметра: SourceFile, TargetFile, SourceDisplayName (необязательно), TargetDisplayName (необязательно).|  
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Регистрирует шаблоны проектов или элементов, которые находятся в папке *\<каталог_установки_Visual_Studio>* \Common7\IDE\ProjectTemplates или *\<каталог_установки_Visual_Studio>* \Common7\IDE\ItemTemplates, чтобы они были доступны в диалоговых окнах **Создание проекта** и **Добавление нового элемента**.<br /><br /> **Devenv /InstallVSTemplates**|  
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Позволяет указать файл для приема ошибок во время сборки.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|  
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Проект, который требуется собрать, очистить или развернуть. Этот параметр можно использовать, только если указан параметр /build, /rebuild, /clean или /deploy.|  
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Задает конфигурацию проекта, которую требуется собрать или развернуть. Этот параметр можно использовать, только если указан параметр /project.|  
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Выполняет очистку, а затем сборку указанного решения или проекта согласно конфигурации заданного решения.|  
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Восстанавливает параметры Visual Studio по умолчанию. При необходимости выполняет сброс параметров в соответствии с указанным файлом VSSETTINGS.|  
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Предписывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в системе и проверить наличие изменений в кэше MEF.|  
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Обновляет указанный файл решения и все его файлы проектов либо указанный файл проекта до текущих форматов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для этих файлов.|  
  
## <a name="see-also"></a>См. также раздел  
 [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)
