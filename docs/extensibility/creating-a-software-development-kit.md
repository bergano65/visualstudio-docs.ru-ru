---
title: Создание пакета средств разработки программного обеспечения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55b62ac0ac448023793f511389146ebb1b07da0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109182"
---
# <a name="creating-a-software-development-kit"></a>Создание пакета средств разработки для программного обеспечения
Пакет средств разработки программного обеспечения (SDK) — это коллекция интерфейсов API, который можно ссылаться как одного элемента в Visual Studio. **Диспетчер ссылок** диалоговом окне приводится список всех пакетов SDK, относящиеся к проекту. При добавлении в проект пакет SDK, API-интерфейсы доступны в Visual Studio.  
  
 Существует два типа пакетов SDK:  
  
-   Пакет SDK платформ — обязательные компоненты для разработки приложений для платформы. Например [!INCLUDE[win81](../debugger/includes/win81_md.md)] пакета SDK, необходимые для разработки [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  
  
-   Пакет SDK расширения являются необязательными компонентами, расширить платформу, но не обязательно при разработке приложений для этой платформы.  
  
 В следующих разделах описаны общие инфраструктуры пакеты SDK и как создать пакет SDK для платформы и пакета SDK расширения.  
  
-   [Пакет SDK платформ](#PlatformSDKs)  
  
-   [Пакет SDK расширения](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> Пакет SDK платформ  
 Пакет SDK платформ, необходимы для разработки приложений для платформы. Например [!INCLUDE[win81](../debugger/includes/win81_md.md)] требуется пакет SDK для разработки приложений для [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Установка  
 Все пакеты SDK для платформы, которые будут устанавливаться в пакеты SDK HKLM\Software\Microsoft\Microsoft\\\v [TPI] [TPV]\\ @InstallationFolder = [пакет SDK для корневой]. Соответственно [!INCLUDE[win81](../debugger/includes/win81_md.md)] в HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 установлен пакет SDK.  
  
### <a name="layout"></a>Макет  
 Пакет SDK платформ будет иметь следующий результат:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Узел|Описание|  
|----------|-----------------|  
|Папка "Ссылки"|Содержит двоичные файлы, содержащие интерфейсы API, которые могут быть спроектированы для. Могут включать файлы метаданных Windows (WinMD) или сборки.|  
|DesignTime папки|Содержит файлы, которые нужны только во время предварительного-run или отладки. Могут включать XML-документы, библиотеки, заголовки, двоичные файлы во время разработки для элементов, MSBuild артефакты и так далее<br /><br /> Документы XML в идеальном случае помещается в папку \DesignTime, но документы XML для ссылок будут размещаться рядом с файлом ссылку в Visual Studio. Например, XML-документации \References ссылку\\[config]\\[arch]\sample.dll будет \References\\[config]\\[arch]\sample.xml и локализованная версия этого документа будут \References\\[config]\\[arch]\\[locale]\sample.xml.|  
|Папка конфигурации|Может существовать только три папки: отладка, розничной торговли и CommonConfiguration. Авторы пакета SDK можно установить свои файлы в CommonConfiguration, если следует использовать тот же набор файлов пакета SDK независимо от конфигурации, в которую будет использовать пакет SDK для потребителей.|  
|Архитектура папки|Может существовать ни одна папка поддерживаемой архитектуры. Visual Studio поддерживает следующих архитектур: x86, x64, ARM и neutral. Примечание: Win32 сопоставляется x86, а для нейтрального AnyCPU.<br /><br /> MSBuild ищет только в рамках \CommonConfiguration\neutral пакеты SDK платформ.|  
|SDKManifest.xml|Этот файл описывает, как Visual Studio следует использовать пакет SDK. Посмотрите на манифест пакета SDK для [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Отображаемое имя:** значение, которое обозревателя объектов отображаются в списке просмотра.<br /><br /> **PlatformIdentity:** существование этот атрибут сообщает Visual Studio и MSBuild, пакет SDK — это платформа SDK и не должны копироваться ссылки, добавленные из его локально.<br /><br /> **TargetFramework:** этот атрибут используется в Visual Studio, чтобы убедиться, что только проекты, предназначенные одинаковые платформы, как указано в значении этого атрибута можно использовать пакет SDK.<br /><br /> **MinVSVersion:** этот атрибут используется в Visual Studio для использования только на пакеты SDK, применимые к нему.<br /><br /> **Ссылка:** этот атрибут должен быть указано для только ссылки, которые содержат элементы управления. Сведения о том, как указать, является ли ссылка содержит элементы управления см. ниже.|  
  
##  <a name="ExtensionSDKs"></a> Пакет SDK расширения  
 В следующих разделах описаны, что необходимо сделать, чтобы развернуть пакет SDK для расширений.  
  
### <a name="installation"></a>Установка  
 Пакет SDK расширения можно установить для конкретного пользователя или для всех пользователей без указания ключа реестра. Чтобы установить пакет SDK для всех пользователей, используйте следующий путь:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Для установки конкретного пользователя используйте следующий путь:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Если вы хотите использовать в другое расположение, необходимо выполнить одно из следующих действий:  
  
1.  Укажите его в раздел реестра:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     и добавьте подраздел (по умолчанию), который имеет значение `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Добавьте свойство MSBuild `SDKReferenceDirectoryRoot` в файл проекта. Значение этого свойства — semi точка с запятой список каталогов, в которых находятся пакеты SDK расширений, ссылка на который.  
  
### <a name="installation-layout"></a>Структуру установки  
 Пакет SDK расширения имеют следующие структуру установки:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< SDKName\>\\< SDKVersion\>: имя и версия пакета SDK является производным от соответствующего имена папок в пути к корню SDK расширения. MSBuild использует это удостоверение, чтобы найти пакет SDK на диске и Visual Studio отображает это удостоверение в **свойства** окна и **диспетчер ссылок** диалогового окна.  
  
2.  Папка ссылок: двоичные файлы, которые содержат API-интерфейсы. Это могут быть файлы метаданных Windows (WinMD) или сборки.  
  
3.  Откройте папку Redist: файлов, которые необходимы для выполнения и отладки и должен получить упакованы как часть приложения пользователя. Все двоичные файлы должны находиться под \redist\\< config\>\\< arch\>, и двоичными именами должны иметь следующий формат для обеспечения уникальности:  **\<компании >.\< продукта >. \<назначение >. \<расширения >**. Например, Microsoft.Cpp.Build.dll. Все файлы с именами, которые могут конфликтовать с именами файлов от других пакетов SDK (например, файлы javascript, css, pri, xaml, png и jpg) должны находиться под \redist\\< config\>\\< arch\> \\< sdkname\>\ Кроме файлов, связанные с XAML, элементы управления. Эти файлы должны находиться под \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  DesignTime папки: файлы, которые необходимо только до-run и отлаживать времени и не должен быть упакованы как часть приложения пользователя. Это могут быть документы XML, библиотеки, заголовки, двоичные файлы во время разработки для элементов, MSBuild артефакты и т. д. Любой пакет SDK, который предназначен для потребления в собственном проекте должна иметь *SDKName*PROPS-файл. Ниже показан пример этого типа файла.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     Справочник по XML-документов, помещаются в файл ссылки. Например, ссылка документ XML для **\References\\< config\>\\< arch\>\sample.dll** сборка **\References\\ < config\>\\< arch\>\sample.xml**, и локализованная версия этого документа — **\References\\< config\>\\< Архитектура\>\\< языкового стандарта\>\sample.xml**.  
  
5.  Папка конфигурации: тремя подпапками: отладка, розничной торговли и CommonConfiguration. Авторы пакета SDK можно разместить свои файлы в CommonConfiguration, если следует использовать тот же набор файлов пакета SDK независимо от конфигурации, целевым объектом-получателем SDK.  
  
6.  Архитектура папки: поддерживаются следующие архитектур: x86, x64, ARM, нейтральную. Win32 сопоставляется x86, а AnyCPU для нейтральной.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Этот файл описывает, как Visual Studio следует использовать пакет SDK. Пример.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Ниже представлены элементы файла.  
  
1.  Отображаемое имя: значение, которое появляется в диспетчере ссылок, обозревателя решений, обозреватель объектов и других местах в пользовательском интерфейсе для Visual Studio.  
  
2.  ProductFamilyName: Общая SDK название продукта. Например [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK называется «Microsoft.WinJS.1.0» и «Microsoft.WinJS.2.0», которые относятся к одному семейству семейства продуктов SDK, «Microsoft.WinJS». Этот атрибут позволяет Visual Studio и MSBuild для создания этого подключения. Если этот атрибут не существует, имя пакета SDK используется как имя семейства продуктов.  
  
3.  FrameworkIdentity: указана зависимость от одного или нескольких библиотек компонентов Windows, значение этого атрибута помещается в манифест приложения потребителя. Этот атрибут применяется только к библиотеки компонентов Windows.  
  
4.  TargetFramework: задает пакеты SDK, доступных в диспетчере ссылок и панель элементов. Это список разделенных точкой с запятой моникеров целевой платформы, например «.NET Framework, версия = v2.0; .NET Framework, версия = v4.5.1». Если указано несколько версий одной целевой версии .NET framework, диспетчер ссылок использует указанный Минимальная версия для целей фильтрации. Например если «.NET Framework, версия = v2.0; .NET Framework, версия = v4.5.1» указано, будет использовать диспетчер ссылок «.NET Framework, версия = v2.0». Если указан профиль целевой платформы, только этот профиль будет использоваться диспетчером ссылку для целей фильтрации. Например, если» Silverlight, версия = версии 4.0, профиль = WindowsPhone» указано, диспетчер ссылок фильтрует только в профиле Windows Phone; проект, предназначенный для полной платформы Silverlight 4.0 не см. в SDK в диспетчере ссылок.  
  
5.  MinVSVersion: минимальная версия Visual Studio.  
  
6.  MaxPlatformVerson: Максимальная целевая версия платформы должен использоваться для указания версии платформы, на которых ваш пакет SDK расширений не будут работать. Например пакет среды выполнения Microsoft Visual C++ v11.0 должны ссылаться только проекты Windows 8. Таким образом MaxPlatformVersion проект Windows 8 — 8.0. Это означает, что диспетчер ссылок отфильтровывает пакет среды выполнения Microsoft Visual C++ для проекта Windows 8.1 и MSBuild вызывает ошибку при [!INCLUDE[win81](../debugger/includes/win81_md.md)] проект ссылается на него. Примечание: этот элемент поддерживается начиная с [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: Указывает, пакеты SDK, которые доступны в диспетчере ссылок, указав применимые типы проектов Visual Studio. Распознаются девять значений: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, управляемый и машинный код. Разработчику пакета SDK можно использовать и ("+"), или («&#124;»), а не («!») операторы, можно указать только область типов проектов, которые применяются в пакет SDK.  
  
     WindowsAppContainer идентифицирует проекты для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  
  
8.  SupportPrefer32Bit: Поддерживаемыми значениями являются «True» и «False». Значение по умолчанию — «True». Если значение равно «False», MSBuild возвращает ошибку для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] проектов (или предупреждения для проектов настольных компьютеров) Если проект, который ссылается на пакет SDK содержит Prefer32Bit включена. Дополнительные сведения о Prefer32Bit см. в разделе [страница построения, конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md) или [компиляция, конструктора проектов (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: архитектур, которые пакет SDK поддерживает список разделенных точкой с запятой. MSBuild отображает предупреждение, если целевая архитектура пакета SDK в потребителе проекта не поддерживается. Если этот атрибут не указан, MSBuild никогда не отображает этот тип предупреждения.  
  
10. SupportsMultipleVersions: Если этот атрибут имеет значение **ошибка** или **предупреждение**, MSBuild показывает, что тот же проект не может ссылаться несколько версий одного семейства пакета SDK. Если этот атрибут не существует или имеет значение **Разрешить**, MSBuild не отображает этот тип ошибки или предупреждения.  
  
11. AppX: Указывает путь к пакетам приложений для библиотеки компонентов Windows на диске. Это значение передается в компонент регистрации библиотеки компонентов Windows во время локальной отладки. Согласно соглашению об именовании для имени файла  **\<компании >.\< Продукта >. \<Архитектура >. \<Configuration >. \<Версии > .appx**. Конфигурации и архитектуре являются необязательными в имени атрибута и значение атрибута, если они не применяются в библиотеку компонентов Windows. Это значение применимо только к библиотеки компонентов Windows.  
  
12. CopyRedistToSubDirectory: Указывает, где следует копировать файлы в папке \redist относительно корневого каталога пакета приложения (то есть **размещение пакета** выбранной в мастере создания пакетов приложений) и корня структуры среды выполнения. Расположение по умолчанию является корневым F5 макета и пакет приложения.  
  
13. DependsOn: Список SDK удостоверений, которые определяют пакеты SDK, от которых зависит данный пакет SDK. Этот атрибут присутствует в области сведений щелкните Диспетчер ссылок.  
  
14. MoreInfo: URL-адрес веб-страницы, которая предоставляет справку и Дополнительные сведения. Это значение используется в ссылке подробнее в правой панели диспетчера ссылок.  
  
15. Тип регистрации: указывает регистрации WinMD в манифесте приложения и является обязательным для собственного WinMD, в которой имеет реализацию аналогом библиотеки DLL.  
  
16. Ссылка на файл: указан для только эти ссылки, содержать элементы управления или собственные файлы Winmd. Сведения о том, как указать, содержит ли ссылка элементов см. в разделе [Указание расположения элементов панели элементов](#ToolboxItems) ниже.  
  
##  <a name="ToolboxItems"></a> Указание расположения элементов панели инструментов  
 Элемент ToolBoxItems схемы SDKManifest.xml указывает категории и расположению элементов области элементов на платформе и пакет SDK расширения. В следующих примерах для указания других мест. Это применимо для ссылки на WinMD или DLL.  
  
1.  Разместите элементы управления в категорию области элементов по умолчанию.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Разместите элементы управления в группе имя определенной категории.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Разместите элементы управления в области определенной категории.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Поместите элементы управления в другую категорию имен в Visual Studio и Blend.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Перечислить определенных элементов управления по-разному в Visual Studio и Blend.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Перечислить определенных элементов управления и поместите их в общий путь Visual Studio или только в группе все элементы управления.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Перечислить определенных элементов управления и отображать только определенный набор ChooseItems без них, в области элементов.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)