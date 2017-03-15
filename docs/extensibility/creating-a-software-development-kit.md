---
title: "Создание средств разработки программного обеспечения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 54
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1d5ea891137bff643ebfcb67cd739aefeb74c2df
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-software-development-kit"></a>Создание средств разработки программного обеспечения
Пакет средств разработки программного обеспечения (SDK) — это совокупность интерфейсы API, который можно ссылаться как одного элемента в Visual Studio. **Диспетчер ссылок** диалоговом окне перечислены все пакеты SDK, относящихся к проекту. При добавлении пакета SDK в проект, интерфейсы API доступны в Visual Studio.  
  
 Существует два типа пакетов SDK:  
  
-   Обязательные компоненты для разработки приложений для платформы Platform SDK: Например [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK, необходимые для разработки [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  
  
-   Пакет SDK расширения являются необязательными компонентами, расширять платформу, но не обязательно при разработке приложений для этой платформы.  
  
 В следующих разделах описаны общие инфраструктуры пакетов SDK и как создать пакет SDK для платформы и расширения SDK.  
  
-   [Пакеты SDK для платформы](#PlatformSDKs)  
  
-   [Пакет SDK расширения](#ExtensionSDKs)  
  
##  <a name="a-nameplatformsdksa-platform-sdks"></a><a name="PlatformSDKs"></a>Пакеты SDK для платформы  
 Пакеты SDK для платформы необходимы для разработки приложений для платформы. Например [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK, необходимые для разработки приложений для [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Установка  
 Все пакеты SDK для платформы, которые будут устанавливаться в пакеты SDK HKLM\Software\Microsoft\Microsoft\\\v [TPI] [TPV]\\ @InstallationFolder = [пакет SDK для корневой]. Соответственно [!INCLUDE[win81](../debugger/includes/win81_md.md)] в HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 установлен пакет SDK.  
  
### <a name="layout"></a>Макет  
 Пакеты SDK для платформы будет следующая структура:  
  
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
|Папка "Ссылки"|Содержит двоичные файлы, содержащие интерфейсы API, которые могут быть спроектированы с. Они включают файлы метаданных Windows (WinMD) или сборки.|  
|DesignTime папки|Содержит файлы, которые необходимы только во время предварительного-run и отладки. Они могут включать документы XML, библиотеки, заголовки, двоичные файлы элементов во время разработки, MSBuild артефакты и так далее<br /><br /> Документы XML в идеале, следует поместить в папку \DesignTime, но документы XML для ссылок будут размещаться рядом с файлом ссылку в Visual Studio. Например, документ XML \References ссылки\\[настройки]\\[arch]\sample.dll будет \References\\[настройки]\\[arch]\sample.xml и локализованная версия этого документа будут \References\\[настройки]\\[arch]\\[locale]\sample.xml.|  
|Папка конфигурации|Может быть только три папки: отладки, розничной торговли и CommonConfiguration. Авторы пакета SDK можно размещать свои файлы в CommonConfiguration, если следует использовать тот же набор файлов пакета SDK независимо от конфигурации, которую будет использовать потребитель SDK.|  
|Архитектура папки|Может существовать папка любой поддерживаемой архитектуре. Visual Studio поддерживает следующих архитектур: x86, x64, ARM и neutral. Примечание: Win32 сопоставляется x86, а для нейтрального AnyCPU.<br /><br /> MSBuild ищет только в условиях \CommonConfiguration\neutral Platform SDK.|  
|SDKManifest.xml|Этот файл описывает, как Visual Studio следует использовать пакет SDK. Просмотрите манифест пакета SDK для [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = “Windows”             PlatformIdentity = “Windows, version=8.1”             TargetFramework = “.NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1”             MinVSVersion = “14.0”>              <File Reference = “Windows.winmd”>                <ToolboxItems VSCategory = “Toolbox.Default” />             </File> </FileList>`<br /><br /> **Отображаемое имя:** значение, которое обозревателя объектов отображаются в списке поиска.<br /><br /> **PlatformIdentity:** существование этого атрибута сообщает Visual Studio и MSBuild, пакет SDK platform SDK и не должны копироваться ссылки, добавленные из его локально.<br /><br /> **TargetFramework:** этот атрибут используется в Visual Studio, чтобы убедиться, что только проектах для одной платформы, как указано в значении этого атрибута можно использовать пакет SDK.<br /><br /> **MinVSVersion:** этот атрибут используется в Visual Studio для использования только пакетов SDK, примените к нему.<br /><br /> **Ссылка:** этот атрибут должен указывать только ссылки, которые содержат элементы управления. Сведения о том, как указать, содержит ли ссылка элементов см. ниже.|  
  
##  <a name="a-nameextensionsdksa-extension-sdks"></a><a name="ExtensionSDKs"></a>Пакет SDK расширения  
 В следующих разделах описаны необходимые для развертывания расширения SDK.  
  
### <a name="installation"></a>Установка  
 Пакет SDK расширения можно установить для конкретного пользователя или для всех пользователей без указания ключа реестра. Чтобы установить пакет SDK для всех пользователей, используйте следующий путь:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Для установки конкретного пользователя используйте следующий путь:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Если вы хотите использовать в другое расположение, необходимо выполнить одно из следующих действий:  
  
1.  Укажите его в разделе реестра:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     и добавьте раздел (по умолчанию), который имеет значение `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Добавьте свойство MSBuild `SDKReferenceDirectoryRoot` в файл проекта. Значение этого свойства является точка с запятой список каталогов, в которых находятся пакеты SDK расширений, ссылка на который полусоединения.  
  
### <a name="installation-layout"></a>Установка макета  
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
  
1.  \\<>\>\\<>\>: имя и версию пакета SDK является производным от соответствующего имена папок в пути к корню пакета SDK расширения. MSBuild использует это удостоверение, чтобы найти пакет SDK на диске, и Visual Studio отображает это удостоверение в **свойства** окна и **диспетчер ссылок** диалогового окна.  
  
2.  Папка ссылок: двоичные файлы, содержащие интерфейсы API. Это могут быть файлы метаданных Windows (WinMD) или сборки.  
  
3.  Откройте папку Redist: файлы, которые необходимы для выполнения и отладки и должен получить упакованы как часть приложения пользователя. Все двоичные файлы должны находиться под \redist\\<>\>\\<>\>, и двоичные имена должны иметь следующий формат для обеспечения уникальности: ** \<компании настроек.\< продукт настроек. \<назначение настроек. \<extension>**. Например, Microsoft.Cpp.Build.dll. Все файлы с именами, которые могут конфликтовать с именами файлов от других SDK (например, файлы javascript, css, pri, xaml, png и jpg) должны находиться под \redist\\<>\>\\<>\>\\<>\>\ Кроме файлов, связанных с XAML элементы управления. Эти файлы должны находиться под \redist\\<>\>\\<>\>\\<>\>\\.  
  
4.  DesignTime папки: файлы, которые необходимо только до-run и отладка времени и не должны быть упакованы как часть приложения пользователя. Это могут быть документы XML, библиотеки, заголовки, двоичные файлы элементов во время разработки, MSBuild артефакты и так далее. Любой пакет SDK, предназначенный для использования в собственном проекте должна иметь *SDKName*PROPS-файл. Ниже приведен пример этого типа файла.  
  
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
  
     Справочник по XML-документы размещаются наряду с файлом ссылки. Например, ссылка документ XML для **\References\\<>\>\\<>\>\sample.dll** сборка **\References\\<>\>\\<>\>\sample.xml**, и является локализованная версия этого документа **\References\\<>\>\\<>\>\\<>\>\sample.xml**.  
  
5.  Папка конфигурации: три подпапки: отладки, розничной торговли и CommonConfiguration. Авторы пакета SDK можно разместить свои файлы в CommonConfiguration, если следует использовать тот же набор файлов пакета SDK независимо от конфигурации, целевые потребителем SDK.  
  
6.  Архитектура папки: поддерживаются следующих архитектур: x86, x64, ARM, neutral. Win32 сопоставляет x86 и AnyCPU сопоставляется с нейтральным.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Этот файл описывает, как Visual Studio следует использовать пакет SDK. Пример.  
  
```  
<FileList>  
DisplayName = “My SDK”  
ProductFamilyName = “My SDKs”  
TargetFramework = “.NETCore, version=v4.5.1; .NETFramework, version=v4.5.1”  
MinVSVersion = “14.0”  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = “True”  
SupportedArchitectures = “x86;x64;ARM”  
SupportsMultipleVersions = “Error”  
CopyRedistToSubDirectory = “.”  
DependsOn = “SDKB, version=2.0”  
MoreInfo = “http://msdn.microsoft.com/MySDK”>  
<File Reference = “MySDK.Sprint.winmd” Implementation = “XNASprintImpl.dll”>  
<Registration Type = “Flipper” Implementation = “XNASprintFlipperImpl.dll” />  
<Registration Type = “Flexer” Implementation = “XNASprintFlexerImpl.dll” />  
<ToolboxItems VSCategory = “Toolbox.Default” />  
</File>  
</FileList>  
```  
  
 Ниже представлены элементы файла.  
  
1.  Отображаемое имя: значение, которое появляется в диспетчере ссылок, обозреватель решений, обозреватель объектов и другие расположения в пользовательском интерфейсе Visual Studio.  
  
2.  ProductFamilyName: Общая SDK название продукта. Например [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK называется «Microsoft.WinJS.1.0» и «Microsoft.WinJS.2.0», которые относятся к одному семейству семейства продуктов SDK, «Microsoft.WinJS». Этот атрибут позволяет Visual Studio и MSBuild, чтобы сделать это подключение. Если этот атрибут не существует, имя SDK используется как имя семейства продуктов.  
  
3.  FrameworkIdentity: задает зависимость на один или несколько библиотек компонентов Windows, значение этого атрибута помещается в манифест принимающего приложения. Этот атрибут применяется только к библиотеки компонентов Windows.  
  
4.  TargetFramework: задает пакеты SDK, доступных в диспетчере ссылок и панель элементов. Это список разделенных точкой с запятой моникеров целевой платформы, например «.NET Framework, версия = v2.0; .NET Framework, версия = v4.5.1». Если указаны несколько версий одной целевой версии .NET framework, диспетчер ссылок использует минимально указанной версии для целей фильтрации. Например если «.NET Framework, версия = v2.0; .NET Framework, версия = v4.5.1» указано, будет использовать диспетчер ссылок» .NET Framework, версия = v2.0». Если указан профиль целевой платформы, только этот профиль будет использоваться диспетчером ссылку для целей фильтрации. Например, если «Silverlight, версия = v4.0 профиль = WindowsPhone» указано, диспетчер ссылок фильтры только в профиле Windows Phone; проект, предназначенный для полной платформы Silverlight 4.0 не отображается в диспетчере ссылок SDK.  
  
5.  MinVSVersion: минимальная версия Visual Studio.  
  
6.  MaxPlatformVerson: Максимальная целевая версия платформы следует использовать для указания версии платформы, на которых расширение SDK не будет работать. Например v11.0 пакета Microsoft Visual C++ среды выполнения должны ссылаться только проекты Windows 8. Таким образом MaxPlatformVersion проект Windows 8 — 8.0. Это означает, что диспетчер ссылок для фильтрации пакета среды выполнения Microsoft Visual C++ для проекта Windows 8.1 и MSBuild вызывает ошибку при [!INCLUDE[win81](../debugger/includes/win81_md.md)] проект ссылается на него. Примечание: этот элемент поддерживается начиная с [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: задает пакеты SDK, доступных в диспетчере ссылок, указав применимые типы проектов Visual Studio. Распознаются девять значений: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, управляемый и машинный. Автор SDK можно использовать и («+ "), или («|»), а не («!») операторы, можно указать только область типов проектов, которые применяются к пакету SDK.  
  
     WindowsAppContainer определяет проекты для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  
  
8.  SupportPrefer32Bit: Поддерживаемые значения — «ИСТИНА» и «False». Значение по умолчанию — «ИСТИНА». Если имеет значение «False», MSBuild возвращает сообщение об ошибке для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] проектов (или предупреждения для проектов настольных компьютеров) Если проект, который ссылается на пакет SDK содержит Prefer32Bit включен. Дополнительные сведения о Prefer32Bit см. в разделе [страница построения, конструктор проектов (C#)](../ide/reference/build-page-project-designer-csharp.md) или [компиляция, конструктор проектов (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: точка с запятой список с разделителями архитектур, поддерживаемых в пакете SDK. MSBuild отображает предупреждение, если целевой архитектуры пакета SDK в принимающем проекте не поддерживается. Если этот атрибут не указан, MSBuild никогда не отображает этот тип предупреждения.  
  
10. SupportsMultipleVersions: Если этот атрибут имеет значение **ошибка** или **предупреждение**, MSBuild показывает, что тот же проект не может ссылаться несколько версий в одном семействе SDK. Если этот атрибут не существует или имеет значение **Разрешить**, MSBuild не отображает этот тип ошибки или предупреждения.  
  
11. AppX: путь к пакеты приложений для библиотеки компонентов Windows на диске. Это значение передается в компонент регистрации библиотеки компонентов Windows во время локальной отладки. Соглашение об именах для имени файла — ** \<компании настроек.\< Продукт настроек. \<Архитектура настроек. \<Конфигурации настроек. \<Версии настроек .appx**. Конфигурация и архитектура являются необязательными в имя атрибута и значение атрибута, если они не относятся к библиотеки компонентов Windows. Это значение применимо только к библиотекам компонентов Windows.  
  
12. CopyRedistToSubDirectory: Указывает, куда будут скопированы файлы в папке \redist относительно корневого каталога пакета приложения (то есть, **расположение пакета** выбрана в мастере создания пакетов приложений) и корневым элементом макета среды выполнения. Расположение по умолчанию является корнем пакет приложения и макет F5.  
  
13. DependsOn: Список удостоверений SDK, определяющие пакеты SDK, от которых зависит данный пакет SDK. Этот атрибут присутствует в области сведений щелкните Диспетчер ссылок.  
  
14. Дополнительная информация: URL-адрес веб-страницы, предоставляющий, справки и Дополнительные сведения. Это значение используется в ссылке подробнее в правой области диспетчер ссылок.  
  
15. Тип регистрации: указывает регистрации WinMD в манифесте приложения и является обязательным для собственного WinMD, с реализацией аналог DLL.  
  
16. Ссылка на файл: для только те ссылки, которые содержат элементы управления или собственные файлы Winmd, указана. Сведения о том, как указать, содержит ли ссылка элементов в разделе [Указание расположения элементов панели элементов](#ToolboxItems) ниже.  
  
##  <a name="a-nametoolboxitemsa-specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Указание расположения элементов  
 Элемент ToolBoxItems схемы SDKManifest.xml указывает категорию и расположение элементов в платформы и пакетах SDK расширений. В следующих примерах для указания других мест. Это относится к ссылкам на WinMD или DLL.  
  
1.  Элементы управления можно поместить в категорию области элементов по умолчанию.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Default”/>       
    </File>  
    ```  
  
2.  Поместите элементы управления в группе имя определенной категории.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory= “MyCategoryName”/>  
    </File>  
    ```  
  
3.  Поместите элементы управления в области определенной категории.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = “Data”>  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Поместите элементы управления в другую категорию области в Blend и Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph” BlendCategory = “Controls/sample/Graph”>   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Перечислить определенные элементы управления по-разному в Blend и Visual Studio.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = “Controls/sample/Graph”>  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Перечислить определенные элементы управления и поместить их в общий путь Visual Studio или только в группе все элементы управления.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Common”>  
        <ToolboxItems />  
        <ToolboxItems VSCategory = “Toolbox.All”>  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Перечислить определенные элементы управления и Показать только определенный набор в ChooseItems без них, в области элементов.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.ChooseItemsOnly”>  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание пакета SDK с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)
