---
title: "Пошаговое руководство. Создание среды построения из нескольких компьютеров | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "среда построения, MSBuild"
  - "MSBuild, построение на нескольких компьютерах"
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Пошаговое руководство. Создание среды построения из нескольких компьютеров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создать среду построения внутри организации путем установки Visual Studio на главном компьютере, а затем скопировать различных файлов и параметров на другом компьютере, способное участвовать в построениях.  Нет необходимости задавать Visual Studio на другом компьютере.  
  
 Этот документ не совещается права распространение программного обеспечения извне или реализовывать среды построения сторонние разработчики.  
  
||  
|-|  
|Отказ от ответственности<br /><br /> Этот документ предоставляется в исходном виде» и «.  Пока рекомендуется выполнить действия, описанные здесь не исчерпывающе, можно выполнить каждую конфигурацию.  Мы попытаемся сохранить документ с текущей выученная любые дополнительные сведения.  Сведения и представления выраженные в этом документе, включая URL\-адреса и ссылки на другие веб\-сайта Интернета, могут изменяться без предварительного уведомления.  Корпорация Майкрософт не выполняет никакой гарантии, express или неявно, по отношению к сведениям, предоставленным здесь.  При носите риск ее использования.<br /><br /> Этот документ не предоставляет возможность законными всеми правами любая интеллектуальная свойство в любом продукт Майкрософт.  Можно скопировать и использовать этот документ для вашей внутренней, цели ссылки.<br /><br /> Решение не установлено для Microsoft все предложения, комментарии или другой обратной связи \(«отзыв»\), связанная с данного документа.  Однако любой необходимо предоставить отзыв добровольно может использоваться в продуктах Майкрософт и соответствующие спецификации или другой документации вместе предложения «\(Майкрософт\)», в свою очередь, могут включать на другими сторонними разработчиками разрабатывать свои продукты.  Соответственно, если присвоить отзыв Майкрософт в любой версии этого документа и предложений, Майкрософт, где они применяются, соглашаетесь: \(A\) Майкрософт может свободно использовать, создается, лицензия, распределяет; в противном случае коммерциализирует отзывы в любой предлагать Майкрософт; \(B\) также присвоить сторонних производителей, без обязанностей, только те патентные права, необходимые " другие продукты или использовать интерфейс с любыми определенными частями продуктов Майкрософт, включающих отзывы; и \(C\), не позволит любому отзыву Майкрософт \(I\), есть причины верить подлеубежите любой патент, авторском праве или другие заявка интеллектуальной право собственности или любого сторонние; или \(ii\) темы к условий лицензии, строки какого\-либо Майкрософт предлагая включение или производного от того отзыва или другой интеллектуальная собственность корпорации Майкрософт, быть лицензированным к или иным общим с любым сторонним разработчиком.|  
  
 В данном пошаговом руководстве было проверяется для следующих операционных систем, путем выполнения MSBuild из командной строки и с помощью Team Foundation.  
  
-   Windows 8 \(x86 и x64\)  
  
-   Windows 7 Максимальная  
  
-   Стандарт Windows Server 2008 R2  
  
 По завершении инструкции в данном пошаговом руководстве можно использовать компьютерная среды построения этих типов приложений:  
  
-   Классические приложения C, C\+\+, использующие Windows SDK 8  
  
-   Классические приложения Visual Basic или C\# этот целевой объект .NET Framework 4.5  
  
 Компьютерную среды нельзя использовать для создания этих типов приложений:  
  
-   приложения [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].  Для построения приложения [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] необходимо настроить Visual Studio на компьютере построения.  
  
-   Классические приложения, целевой объект .NET Framework 4 или более ранней версии.  Для создания этих типов приложений необходимо задать или Visual Studio или базовые сборки и средства .NET \(из Windows SDK 7.1\) на компьютере построения.  
  
 Это пошаговое руководство состоит из следующих частей:  
  
-   [Установить программное обеспечение на компьютерах](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
-   [Копирование файлов из главного компьютера на компьютер построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
-   [Создание параметров реестра](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
-   [Переменные среды параметра на компьютере построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
-   [MSBuild поместить сборку в глобальный кэш сборок (GAC) на компьютере построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
-   [Создание проектов](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
-   [Создание среды построения, чтобы ее можно проверить в систему управления версиями](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## Обязательные компоненты  
  
-   Лицензированное копию Visual Studio Ultimate, Visual Studio Premium, или Visual Studio Professional  
  
-   Копия 4.5.1 платформы .NET Framework, которые можно загрузить с веб\-сайта [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software).  
  
##  <a name="InstallingSoftware"></a> Установить программное обеспечение на компьютерах  
 Прежде всего, создайте главный компьютер, а затем настройте компьютер построения.  
  
 Путем установки Visual Studio на главном компьютере, необходимо создать файлы и параметры, которые были скопированы на компьютер построения позже.  Можно будет задавать Visual Studio на компьютере с архитектурой x86 или x64, но архитектура компьютера построения должна соответствовать архитектуре главного компьютера.  
  
#### Установить программное обеспечение на компьютерах  
  
1.  В главном компьютере, задайте Visual Studio.  
  
2.  На компьютере построения, платформу .NET Framework 4.5. Чтобы убедиться, что он задает, убедитесь, что значение начинается HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\NET .NET Framework Setup\\NDP\\v4\\Full@Version раздела реестра с «4.5».  
  
##  <a name="CopyingFiles"></a> Копирование файлов из главного компьютера на компьютер построения  
 В этом разделе рассматриваются копирование определенных файлов, компиляторам, средств построения, активов MSBuild и параметры реестра из главного компьютера на компьютер построения.  Эти инструкции высказывать установленное Visual Studio в расположении по умолчанию в главном компьютере; если необходимо задать в другом расположении, настройка инструкции соответственно.  
  
-   X86 на компьютере, расположение по умолчанию C: \\Program Files\\Microsoft Visual Studio 11.0\\  
  
-   На 64\-разрядных компьютерах, расположение по умолчанию C: \\Microsoft Visual Studio 11.0\\ файлов \\Program \(x86\)  
  
 Обратите внимание, что имя папки Program Files зависит от операционной системы, задания.  X86 на компьютере, имя \\Program Files\\; на 64\-разрядных компьютерах, имя \\ файлов \\Program \(x86\).  Независимо от системной архитектуры, в данном пошаговом руководстве относится к папке Program Files как %ProgramFiles%.  
  
> [!NOTE]
>  На компьютере построения, все соответствующие файлы должны находиться на том же диске; однако буква диска для этого диска может отличаться от буква диска для диска, в котором Visual Studio задано в главном компьютере.  В любом случае необходимо указать расположение файлов при создании записи реестра, как описано далее в этом документе.  
  
#### Копирование файлов Windows SDK в систему компьютера построения  
  
1.  Если есть только, Windows SDK для Windows 8 устанавливается, скопировать эти папки рекурсивно из главного компьютера на компьютер построения.  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\bin\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Catalogs\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\DesignTime\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\include\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Lib\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Redist\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\References\\  
  
     Если также имеется эти другие основные Windows 8,…  
  
    -   Оценка Microsoft Windows и комплект развертывания  
  
    -   Комплект драйвера Microsoft Windows  
  
    -   Комплект центра оборудования Microsoft Windows  
  
     … они могут поместить файлы в папке %ProgramFiles%\\Windows Kits\\8.0\\, перечисленных в предыдущем шаге, и их условия лицензии не может разрешить права на сервере построений для этих файлов.  Проверка условия лицензии для каждого набора файлов Windows для проверки могут быть скопированы ли файлы на компьютер построения.  Если условия лицензии не позволяют права на сервере построений, удалите файлы с компьютера построения.  
  
2.  Скопируйте следующие папки рекурсивно из главного компьютера на компьютер построения.  
  
    -   %ProgramFiles%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\  
  
    -   %ProgramFiles%\\Common Files\\Merge Modules\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\ProjectComponents\\  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\V110\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETCore\\v4.5\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETFramework\\v4.5\\  
  
3.  Скопируйте эти файлы из главного компьютера на компьютер построения.  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msobj110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdb110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbcore.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbsrv.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msvcdis110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\makehm.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\VCVarsQueryRegistry.bat  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\vsvars32.bat  
  
4.  Следующие библиотеки времени выполнения C Visual C\+\+, необходимы только при выполнении выходные данные построения на построение компьютерн для примера, в рамках автоматизированного тестирования.  Файлы обычно находятся во вложенных папках в папке %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x86\\ или %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x64\\, в зависимости от системной архитектуры.  В системах x86, скопируйте x86 бинарный в папку \\Windows\\System32\\.  На 64\-разрядных системах скопируйте в папку Windows\\SysWOW64\\ бинарный x86 и x64 бинарный в папку Windows\\System32\\.  
  
    -   \\Microsoft.VC110.ATL\\atl110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcp110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcr110.dll  
  
    -   \\Microsoft.VC110.CXXAMP\\vcamp110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110u.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110u.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110chs.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110cht.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110enu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110esn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110fra.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110ita.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110jpn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110kor.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110rus.dll  
  
    -   \\Microsoft.VC110.OPENMP\\vcomp110.dll  
  
5.  Скопируйте только следующие файлы из папки \\Debug\_NonRedist\\x86\\ или \\Debug\_NonRedist\\x64\\ в систему компьютера построения, как описано в разделе [Подготовка тестового компьютера для выполнения исполняемого файла отладки](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable).  Никакие другие файлы не могут быть скопированы.  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcp110d.dll  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcr110d.dll  
  
    -   \\Microsoft.VC110.DebugCXXAMP\\vcamp110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110ud.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110ud.dll  
  
    -   \\Microsoft.VC110.DebugOpenMP\\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> Создание параметров реестра  
 Необходимо создать записи реестра, чтобы настроить параметры для MSBuild.  
  
#### Создание параметров реестра  
  
1.  Указать родительскую папку для записей реестра.  Все записи реестра создаются в тот же родительским ключом.  X86 на компьютере, родительский ключ HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.  На 64\-разрядных компьютерах родительский ключ HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.  Независимо от системной архитектуры, в данном пошаговом руководстве относится к родительскому ключу в качестве %RegistryRoot%.  
  
    > [!NOTE]
    >  Если архитектура основного компьютера отличается от механизма компьютера построения, следует использовать соответствующий родительский ключ на каждом компьютере.  Это особенно важно при автоматизируете процесса экспорта.  
    >   
    >  Кроме того, при использовании другую букву диска на компьютере построения, используемые в главном компьютере убедитесь изменения значений записей реестра для сопоставления.  
  
2.  Создайте следующие записи реестра на компьютере построения.  Во всех этих записей строки \(\=\= «REG\_SZ» типа в реестре\).  Установите значения для этих записей совпадает с значения соответствующих записей в главном компьютере.  
  
    -   %RegistryRoot%\\.NETFramework\\v4.0.30319\\AssemblyFoldersEx\\VCMSBuild открытый Assemblies@ \(по умолчанию\)  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools\-x86@InstallationFolder  
  
    -   каталоги %RegistryRoot% \\VisualStudio\\11.0@Source  
  
    -   %RegistryRoot% \\VisualStudio\\11.0\\Setup\\VC@ProductDir  
  
    -   %RegistryRoot% \\VisualStudio\\SxS\\VC7@FrameworkDir32  
  
    -   %RegistryRoot% \\VisualStudio\\SxS\\VC7@FrameworkDir64  
  
    -   %RegistryRoot% \\VisualStudio\\SxS\\VC7@FrameworkVer32  
  
    -   %RegistryRoot% \\VisualStudio\\SxS\\VC7@FrameworkVer64  
  
    -   %RegistryRoot% \\VisualStudio\\SxS\\VC7@11.0  
  
    -   %RegistryRoot% \\VisualStudio\\SxS\\VS7@11.0  
  
    -   %RegistryRoot%\\Windows Kits\\Installed Roots@KitsRoot  
  
    -   %RegistryRoot% \\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   %RegistryRoot% \\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   %RegistryRoot% \\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
     На компьютере построения x64, также создать следующую запись реестра и в разделе главный компьютер, чтобы указать, как установить его.  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools\-x64@InstallationFolder  
  
     Если компьютер построения x64 и требуется использовать 64 64\-битных версиях MSBuild, или при использовании службы построения Team Foundation Server на 64\-разрядных компьютерах, необходимо создать следующие записи реестра в собственном 64\-разрядном в реестре.  В разделе главный компьютер, чтобы определить, как настроить эти записи.  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Setup\\VS@ProductDir  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> Переменные среды параметра на компьютере построения  
 Для использования MSBuild на компьютере построения необходимо настроить переменные среды PATH.  Можно использовать vcvarsall.bat установки переменных, или можно вручную настроить их.  
  
#### Использовать vcvarsall.bat для установки переменных среды  
  
-   Откройте окно командной строки на компьютере построения и запуска %Program Files%\\Microsoft Visual Studio 11.0\\VC\\vcvarsall.bat.  Можно использовать аргумент командной строки задать набор инструментов, к use\-x86, собственных x64 или x64 кросс\-компилятора.  Если не задан аргумент командной строки, x86 набор инструментов используется.  
  
     В этой таблице описаны поддерживаемые аргументы для vcvarsall.bat:  
  
    |Аргумент Vcvarsall.bat|Компилятор|Архитектура компьютера построения|Архитектура выходных данных сборки|  
    |----------------------------|----------------|---------------------------------------|----------------------------------------|  
    |x86 \(по умолчанию\)|32\-разрядный, машинный|x86, x64|x86|  
    |x86\_amd64|перекрестные x64|x86, x64|x64|  
    |amd64|собственные x64|x64|x64|  
  
     Если выполняется успешн\-, не выводит сообщение об ошибке vcvarsall.bat, показывать\- можно пропустить следующий шаг и продолжить работу в подразделе [MSBuild поместить сборку в глобальный кэш сборок (GAC) на компьютере построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) этого документа.  
  
#### В вручную задать переменных среды  
  
1.  Чтобы вручную настроить среду командной строки, добавьте этот путь в переменной среды PATH.  
  
    -   %Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE  
  
2.  При необходимости можно добавить следующие пути к переменной PATH, чтобы сделать его проще использовать MSBuild для построения решений.  
  
     Если требуется использовать собственное 32 бит MSBuild, добавляет эти пути к переменной PATH:,  
  
    -   средства %Program Files%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0  
  
    -   %windir%\\Microsoft.NET\\Framework\\v4.0.30319  
  
     Если требуется использовать собственное 64 бит MSBuild, добавляет эти пути к переменной PATH:,  
  
    -   %Program Files%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\x64  
  
    -   %windir%\\Microsoft.NET\\Framework64\\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> MSBuild поместить сборку в глобальный кэш сборок \(GAC\) на компьютере построения  
 MSBuild необходимо, чтобы некоторые дополнительные сборки устанавливаются на сборку на компьютере построения.  
  
#### Копировать сборки из главного компьютера и установить их на компьютере построения  
  
1.  Скопируйте следующие сборки из главного компьютера на компьютер построения.  Так как они будут установлены в сборке, не имеет значения, где размещен их на компьютер построения.  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   11.0\\Common7\\IDE\\CommonExtensions\\Microsoft\\VC\\Project\\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll %ProgramFiles%\\Microsoft Visual Studio  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\PublicAssemblies\\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  Чтобы поместить сборку в глобальном кэше сборок, найдите gacutil.exe при построении компьютерном — является типичным, его в %ProgramFiles%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\.  Если не удается найти в этой папке, повторьте шаги, описанные в разделе [Копирование файлов из главного компьютера на компьютер построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) этого пошагового руководства.  
  
     Откройте окно командной строки, выполняемое с правами администратора и этой команде для каждого файла:  
  
     **gacutil \-i \<file\>**  
  
    > [!NOTE]
    >  Перезагрузка может, необходимые для сборки полностью присваивается в сборку.  
  
##  <a name="BuildingProjects"></a> Создание проектов  
 Можно использовать Team Foundation построения проектов и решений [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], или можно создать их в командной строке.  При использовании Team Foundation для построения проектов, он вызывает исполняемый файл MSBuild, который соответствует системной архитектуры.  В командной строке можно использовать или 32 бит или MSBuild 64 бит MSBuild и можно выбрать архитектуры MSBuild с помощью установки переменной среды PATH или непосредственно вызов исполняемый файл MSBuild архитектура\- функции.  
  
 Для использования msbuild.exe в командной строке выполните следующую команду, где *solution.sln* — это местозаполнитель для имени решения.  
  
 **msbuild** *solution.sln*  
  
 Дополнительные сведения о использованию MSBuild из командной строки см. в разделе [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Для построения проектов [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], необходимо использовать «v110» платформу Набор инструментов.  При необходимости изменения файлов проекта [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], можно установить платформу Набор инструментов, с помощью этого аргумента командной строки:  
>   
>  **msbuild** *solution.sln* **\/p:PlatformToolset\=v110**  
  
##  <a name="CreatingForSourceControl"></a> Создание среды построения, чтобы ее можно проверить в систему управления версиями  
 Можно создать среды построения, можно развертывать на разных компьютерах и не требует файлов GAC'ing или изменить параметры реестра.  Следующие шаги только один способ выполнения это.  Преобразование значения этих шагов однозначно характеристикам среды построения.  
  
> [!NOTE]
>  Необходимо отключить дифференциальное построение было tracker.exe не возникает ошибка во время построения.  Чтобы отключить дифференциальное построения, установите этот параметр построения:  
>   
>  **msbuild** *solution.sln* **\/p:TrackFileAccess\=false**  
  
#### Создание среды построения, можно вернуть в систему управления версиями  
  
1.  Создайте каталог «депо» в главном компьютере.  
  
     Следующие действия ссылаются на каталог как %Depot%.  
  
2.  Скопируйте файлы и каталоги, как описано в подразделе [Копирование файлов из главного компьютера на компьютер построения](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) данного пошагового руководства, за исключением вставлять их в каталоге %Depot%, созданные.  Например, скопируйте из %ProgramFiles%\\Windows Kits\\8.0\\bin\\ в %Depot%\\Windows Kits\\8.0\\bin\\.  
  
3.  Если файлы вставлены в %Depot% выполните следующие изменения:  
  
    -   В %Depot%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPP.Targets, \\Microsoft.Cpp.InvalidPlatforms.targets\\, \\Microsoft.cppbuild.targets\\ и \\Microsoft.CppCommon.targets\\, изменяются каждый экземпляр  
  
         AssemblyName\="Microsoft.Build.CppTasks.Common.v110, Version\=4.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a"  
  
         в  
  
         AssemblyFile\="$\(VCTargetsPath11\)Microsoft.Build.CppTasks.Common.v110.dll”.  
  
         Первый именование основывается на сборке. GAC'ed.  
  
    -   В %Depot% \\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPPClean.Targets измените каждый экземпляр  
  
         AssemblyName\="Microsoft.Build.CppTasks.Common.v110, Version\=4.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a"  
  
         в  
  
         AssemblyFile\="$\(VCTargetsPath11\)Microsoft.Build.CppTasks.Common.v110.dll”.  
  
4.  Создайте PROPS файл\- для примера, Partner.AutoImports.props\-and поместите его в корневой папке, содержащей проектов.  Этот файл используется, чтобы задать переменные, используемые MSBuild для поиска различные ресурсы.  Если переменные не заданы этим файлом, они задаются другими файлами PROPS и файлы с расширением TARGETS, зависящие от значений реестра.  Поскольку это не устанавливаем никаких значений реестра, эти переменные являются пустыми и построение приведет к сбою.  Вместо этого добавьте следующее к Partner.AutoImports.props:  
  
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
  
5.  В каждом из файлов проекта добавьте следующую линию в верхней линии, после `<Project Default Targets…>`.  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  Изменение среды командной строки следующим образом:  
  
    -   Задайте Depot\=*location of the Depot directory that you created in step 1*  
  
    -   Set path\=%path%;*location of MSBuild on the computer*;%Depot%\\Windows\\System32;%Depot%\\Windows\\SysWOW64;%Depot%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\  
  
         Для собственного 64\-разрядного построения выберите 64\-разрядному MSBuild.  
  
## См. также  
 [Подготовка тестового компьютера для выполнения исполняемого файла отладки](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)