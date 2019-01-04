---
title: Создание пакета средств разработки программного обеспечения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea506479226ed8585296208064bd3533cf0a5783
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922849"
---
# <a name="create-a-software-development-kit"></a>Создание пакета средств разработки программного обеспечения
Пакет средств разработки программного обеспечения (SDK) — это коллекция интерфейсов API, который можно ссылаться как одного элемента в Visual Studio. **Диспетчер ссылок** диалоговом окне приводится список всех пакетов SDK, относящихся к проекту. При добавлении пакета SDK в проект, интерфейсы API доступны в Visual Studio.  

 Существует два типа пакетов SDK:  

- Пакеты SDK платформы, обязательные компоненты для разработки приложений для платформы. Например [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK, необходимые для разработки [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  

- Пакеты SDK расширения, дополнительные компоненты, которые расширяют платформу, но не обязательно для разработки приложений для данной платформы.  

  В следующих разделах описаны общие инфраструктуры, пакеты SDK и как создать пакет SDK платформы и пакет SDK расширения.  

- [Пакеты SDK для платформы](#PlatformSDKs)  

- [Пакеты SDK расширений](#ExtensionSDKs)  

##  <a name="PlatformSDKs"></a> Пакеты SDK для платформы  
 Пакеты SDK для платформы необходимы для разработки приложений для платформы. Например [!INCLUDE[win81](../debugger/includes/win81_md.md)] требуется пакет SDK для разработки приложений для [!INCLUDE[win81](../debugger/includes/win81_md.md)].  

### <a name="installation"></a>Установка  
 Все пакеты SDK для платформы, которые будут устанавливаться в*пакеты SDK HKLM\Software\Microsoft\Microsoft\\[TPI] \v [TPV]\\ @InstallationFolder = [пакет SDK root]*. Соответственно [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK устанавливается в *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.  

### <a name="layout"></a>Макет  
 Пакеты SDK для платформы будет иметь компоновку, следующие:  

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


| Узел | Описание: |
|------------------------| - |
| *Ссылки на* папки | Содержит двоичные файлы, содержащие интерфейсы API, которые можно было кодировать с. Могут включать файлы метаданных Windows (WinMD) или сборки. |
| *DesignTime* папки | Содержит файлы, которые необходимы только во время предварительного-run и отладки. Могут включать документы XML, библиотеки, заголовки, двоичные файлы времени разработки для элементов, MSBuild артефакты и т. д<br /><br /> Документы XML в идеальном случае помещается в *\DesignTime* папку, но документы XML для ссылок продолжат размещаться вместе с файлом ссылку в Visual Studio. Например, документ XML для ссылки на<em>\References\\[конфигурации]\\[arch]\sample.dll</em> будет *\References\\[конфигурации]\\[arch]\sample.xml*, и локализованная версия этого документа будут *\References\\[конфигурации]\\[атрибут arch]\\[locale]\sample.xml*. |
| *Конфигурация* папки | Может существовать только три папки: *Отладка*, *розничной торговли* и *CommonConfiguration*. Авторы пакета SDK можно поместить свои файлы в *CommonConfiguration* если тот же набор файлов пакета SDK следует использовать, независимо от конфигурации, на которой будет работать потребителя пакета SDK. |
| *Архитектура* папки | Любых поддерживаемых *архитектура* может существовать папка. Visual Studio поддерживает следующие варианты архитектуры: x86, x64, ARM и neutral. Примечание. Win32 сопоставляется x86, а AnyCPU для нейтрального.<br /><br /> MSBuild ищет только при выполнении *\CommonConfiguration\neutral* для пакетов SDK платформы. |
| *SDKManifest.xml* | Этот файл описывает, как Visual Studio следует использовать пакет SDK. Просмотрите манифест, пакет SDK для [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Отображаемое имя:** Значение, в обозревателе объектов отображаются в списке просмотра.<br /><br /> **PlatformIdentity:** Наличие этого атрибута сообщает Visual Studio и MSBuild, что пакет SDK платформы SDK и что ссылки, добавленные из его не следует скопировать локально.<br /><br /> **TargetFramework:** Этот атрибут используется в Visual Studio, чтобы убедиться, что только проекты, предназначенные же платформы, как указано в значении этого атрибута можно использовать пакет SDK.<br /><br /> **MinVSVersion:** Этот атрибут используется в Visual Studio для использования только пакеты SDK, которые применяются к нему.<br /><br /> **Справочные материалы.** Этот атрибут должен быть указано для только эти ссылки, которые содержат элементы управления. Сведения о том, как указать, содержит ли ссылка элементы управления см. в разделе ниже. |

##  <a name="ExtensionSDKs"></a> Пакеты SDK расширений  
 В следующих разделах, что необходимо сделать, чтобы развернуть пакет SDK расширения.  

### <a name="installation"></a>Установка  
 Пакеты SDK расширений можно установить для конкретного пользователя или для всех пользователей без указания ключа реестра. Чтобы установить пакет SDK для всех пользователей, используйте следующий путь:  

 *% Program Files%\Microsoft SDK\<целевую платформу > \v<platform version number>\ExtensionSDKs*  

 Для установки конкретного пользователя используйте следующий путь:  

 *Пакеты SDK %USERPROFILE%\AppData\Local\Microsoft\<целевую платформу > \v<platform version number>\ExtensionSDKs*  

 Если вы хотите использовать другое расположение, необходимо выполнить одно из следующих действий:  

1.  Укажите его в раздел реестра:  

     **Пакеты SDK HKLM\Software\Microsoft\Microsoft\<целевую платформу > \v<platform version number>\ExtensionSDKs\<SDKName >\<SDKVersion >**\  

     и добавьте раздел (по умолчанию), который имеет значение `<path to SDK><SDKName><SDKVersion>`.  

2.  Добавить свойство MSBuild `SDKReferenceDirectoryRoot` в файл проекта. Разделенные точкой с запятой список каталогов, в которых находятся пакеты SDK расширений, создать ссылку на значение этого свойства.  

### <a name="installation-layout"></a>Макета установки  
 Пакеты SDK расширений имеет следующую компоновку установки:  

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

1. \\< SDKName\>\\< SDKVersion\>: название и версия SDK является производным от именами папок в пути к корню SDK расширения. MSBuild использует это удостоверение, чтобы найти пакет SDK на диске, и Visual Studio отображает это удостоверение в **свойства** окна и **диспетчер ссылок** диалоговое окно.  

2. *Ссылки на* папку: двоичные файлы, которые содержат API-интерфейсы. Это могут быть файлы метаданных Windows (WinMD) или сборки.  

3. *Redist* папку: файлов, которые необходимы для среды выполнения и отладки и должны получить упакованы как часть приложения пользователя. Все двоичные файлы должны находиться под *\redist\\< config\>\\< arch\>*, и двоичными именами должны иметь следующий формат, чтобы обеспечить уникальность: *]* \<компании >. \<продукта >. \<цель >. \<расширения ><em>. Например, *Microsoft.Cpp.Build.dll</em>. Все файлы с именами, которые могут конфликтовать с именами файлов из других пакетов SDK (например, файлы javascript, css, pri, xaml, png и jpg) должны находиться под <em>\redist\\< config\>\\< arch\> \\< sdkname\> \* Кроме файлов, связанные с XAML управляет. Эти файлы должны находиться под * \redist\\< config\>\\< arch\>\\< componentname\>\\</em>.  

4. *DesignTime* папки: файлы, которые необходимо только предварительного-run/отладка времени и не должны быть упакованы как часть приложения пользователя. Это могут быть документы XML, библиотеки, заголовки, двоичные файлы времени разработки для элементов, MSBuild артефакты и т. д. Любой пакет SDK, который предназначен для использования собственного проекта должна иметь *SDKName.props* файла. Ниже показан пример этого типа файла.  

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

    Справочник по XML-документов размещаются в каталоге файла ссылки. Например, справочный документ XML для *\References\\< config\>\\< arch\>\sample.dll* сборка является *\References\\ < config\>\\< arch\>\sample.xml*, и локализованная версия этого документа является *\References\\< config\>\\< arch\>\\< языкового стандарта\>\sample.xml*.  

5. *Конфигурация* папку: три вложенные папки: *Отладка*, *розничной торговли*, и *CommonConfiguration*. Авторы пакета SDK можно поместить свои файлы в *CommonConfiguration* когда тот же набор файлов пакета SDK следует использовать, независимо от конфигурации мишенью для потребителя пакета SDK.  

6. *Архитектура* папку: поддерживаются следующие варианты архитектуры: x86, x64, ARM, нейтральную. Win32 сопоставляется x86, а AnyCPU для нейтрального.  

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
MoreInfo = "https://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  

 Ниже представлены элементы файла.  

1. Отображаемое имя: значение, которое появляется в диспетчере ссылок, обозреватель решений, обозреватель объектов и других местах в пользовательском интерфейсе для Visual Studio.  

2. ProductFamilyName: Общее имя продукта SDK. Например [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK называется «Microsoft.WinJS.1.0» и «Microsoft.WinJS.2.0», которые относятся к одному семейству семейства продуктов пакета SDK, «Microsoft.WinJS». Этот атрибут позволяет Visual Studio и MSBuild установить нужное соединение. Если этот атрибут не существует, имя пакета SDK используется как имя семейства продуктов.  

3. FrameworkIdentity: Задает зависимость на один или несколько библиотек компонентов Windows, значение этого атрибута помещается в манифест принимающего приложения. Этот атрибут применяется только к библиотеки компонентов Windows.  

4. TargetFramework: Указывает пакеты SDK, доступные в диспетчере ссылок и панели элементов. Это список разделенных точкой с запятой моникеров целевой платформы, например «.NET Framework, version = версии 2.0; .NET Framework, version = пакету версии 4.5.1». Если указаны несколько версий одной целевой платформы, диспетчер ссылок использует минимально указанную версию для целей фильтрации. Например если «.NET Framework, версия = версии 2.0; .NET Framework, версия = пакету версии 4.5.1» указано, будет использовать диспетчер ссылок «.NET Framework, версия = версии 2.0». Если указан профиль целевой платформы, только этот профиль будет использоваться диспетчером ссылок для целей фильтрации. Например, если «Silverlight, версия = v4.0, профиль = WindowsPhone» указано, диспетчер ссылок фильтрует только в профиле Windows Phone; проект, предназначенный для полной платформы Silverlight 4.0 не видит пакета SDK в диспетчере ссылок.  

5. MinVSVersion: Минимальная версия Visual Studio.  

6. MaxPlatformVerson: Максимальная целевая версия платформы должен использоваться для указания версии платформы, на которых ваш пакет SDK расширений не будет работать. Например пакет среды выполнения Microsoft Visual C++ v11.0 должны ссылаться только проекты Windows 8. Таким образом MaxPlatformVersion проекта Windows 8 — 8.0. Это означает, что диспетчер ссылок отфильтровывает пакета среды выполнения Microsoft Visual C++ для проекта Windows 8.1 и MSBuild вызывает ошибку при [!INCLUDE[win81](../debugger/includes/win81_md.md)] проект ссылается на нее. Примечание: этот элемент поддерживается начиная с версии [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  

7. AppliesTo: Указывает пакеты SDK, доступные в диспетчере ссылок, указав применимые типы проектов Visual Studio. Распознаются девять значений: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, управляемым и машинный код. Автор пакета SDK можно использовать и ("+"), или («&#124;»), а не (»!») Операторы выбора точно области типов проектов, которые применяются к пакету SDK.  

    WindowsAppContainer идентифицирует проекты для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  

8. SupportPrefer32Bit: Поддерживаемые значения: «True» и «False». По умолчанию используется «True». Если значение имеет значение «False», MSBuild возвращает ошибку для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] проектов (или предупреждения для проектов классических приложений) Если в проекте, который ссылается на пакет SDK Prefer32Bit включена. Дополнительные сведения о Prefer32Bit, см. в разделе [страница "сборки" в конструкторе проектов (C#)](../ide/reference/build-page-project-designer-csharp.md) или [страница компиляции, конструктор проектов (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  

9. SupportedArchitectures: Список архитектур, которые поддерживают пакет SDK, разделенных точкой с запятой. MSBuild отображает предупреждение, если целевой архитектуры пакета SDK в потребляющий проект не поддерживается. Если этот атрибут не указан, MSBuild никогда не отображает этот тип предупреждения.  

10. SupportsMultipleVersions: Если этот атрибут имеет значение **ошибка** или **предупреждение**, MSBuild указывает, что тот же проект не может ссылаться на несколько версий пакета SDK для того же семейства. Если этот атрибут не существует или имеет значение **Разрешить**, MSBuild не отображает этот тип ошибки или предупреждения.  

11. AppX: Указывает путь к пакетам приложений для библиотеки компонентов Windows на диске. Это значение передается в компонент регистрации библиотеки компонентов Windows во время локальной отладки. Соглашение об именовании для имени файла  *\<компании >.\< Продукт >. \<Архитектура >. \<Configuration >. \<Версии > .appx*. Конфигурация и архитектура являются необязательными в имя атрибута и значение атрибута, если они не относятся к библиотеки компонентов Windows. Это значение применимо только к библиотеки компонентов Windows.  

12. CopyRedistToSubDirectory: Указывает, где файлы в папке *\redist* папки должны копироваться относительно корня пакета приложения (то есть **размещение пакета** выбранным в **создать пакет приложения** Мастер) и корневым элементом макета среды выполнения. По умолчанию расположением является корень пакета приложения и **F5** макета.  

13. DependsOn: Список идентификаторов SDK, которые определяют пакеты SDK, от которых зависит данный пакет SDK. Этот атрибут появляется в области сведений диспетчера ссылок.  

14. MoreInfo: URL-адрес веб-страницу, которая предоставляет справку и Дополнительные сведения. Это значение используется в ссылке Дополнительные сведения в правой области диспетчера ссылок.  

15. Тип регистрации: Указывает регистрации WinMD в манифесте приложения и является обязательным для собственного WinMD, который имеет реализацию какой DLL.  

16. Ссылка на файл: Указанный для только те ссылки, которые содержат элементы управления или превышают собственных winmd-файлов. Сведения о том, как указать, содержит ли ссылка элементы управления, см. в разделе [укажите расположение элементов панели инструментов](#ToolboxItems) ниже.  

##  <a name="ToolboxItems"></a> Укажите расположение элементов панели инструментов  
 Элемент ToolBoxItems *SDKManifest.xml* схема задает категории и расположению элементов панели инструментов в пакетах SDK для платформы и расширения. В следующих примерах для указания других мест. Это применимо к ссылки WinMD и DLL.  

1.  Разместите элементы управления в категории панели элементов по умолчанию.  

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

4.  Поместите имена различных категорий элементов управления в Blend и Visual Studio.  

    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  

5.  Перечислить определенные элементы управления по-разному в Blend и Visual Studio.  

    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  

6.  Перечислить определенные элементы управления и поместить их в Visual Studio общий путь, или только в группы "все элементы управления".  

    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  

7.  Перечислить определенные элементы управления и Показать только определенной группе в ChooseItems без них, в области элементов.  

    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  

## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создайте пакет SDK, с помощью C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Пошаговое руководство: Создание пакета SDK с помощью C# или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)