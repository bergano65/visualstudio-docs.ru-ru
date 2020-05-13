---
title: Создание комплекта для разработки программного обеспечения (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739594"
---
# <a name="create-a-software-development-kit"></a>Создание комплекта для разработки программного обеспечения

Комплект для разработки программного обеспечения (SDK) представляет собой набор AI, на который можно ссылаться в качестве одного элемента в Visual Studio. В диалоговом окне **справочного менеджера** перечислены все SDK, имеющие отношение к проекту. При добавлении SDK в проект AA доступны в Visual Studio.

Существует два типа SDK:

- Платформа SDK являются обязательными компонентами для разработки приложений для платформы. Например, [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK требуется [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] для разработки приложений.

- Расширение SDK являются дополнительными компонентами, которые расширяют платформу, но не являются обязательными для разработки приложений для этой платформы.

В следующих разделах описывается общая инфраструктура SDK и как создать платформу SDK и расширение SDK.

## <a name="platform-sdks"></a>Пакеты SDK для платформ

Платформы SDK необходимы для разработки приложений для платформы. Например, [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK требуется для [!INCLUDE[win81](../debugger/includes/win81_md.md)]разработки приложений для .

### <a name="installation"></a>Установка

Все платформы SDK будут установлены на *HKLM-Software-Microsoft SDKs\\(TPI)\\ @InstallationFolder - TPV .* В связи [!INCLUDE[win81](../debugger/includes/win81_md.md)] с чем, SDK устанавливается на *HKLM-Software-Microsoft SDKs-Windows-v8.1*.

### <a name="layout"></a>Макет

Платформа SDK имеет следующую компоновку:

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

| Узел | Описание |
|------------------------| - |
| *Папка ссылок* | Содержит файлы, содержащие AAP, которые могут быть закодированы против. К ним могут относиться файлы или сборки Windows Metadata (WinMD). |
| *Папка DesignTime* | Содержит файлы, которые необходимы только во время предварительного запуска/отладки. Они могут включать в себя XML документы, библиотеки, заголовки, Toolbox дизайн времени бинарных файлов, MSBuild артефакты, и так далее<br /><br /> Документы XML, в идеале, будут помещены в папку *«DesignTime»,* но документы XML для ссылок будут по-прежнему размещаться вместе с справочным файлом в Visual Studio. Например, док XML для<em>справочной справки\\«Ссылки» (конфигурация)\\«arch»sample.dll</em> будет *«Справки\\»конфигурация»\\(arch)sample.xml,* а локализованная версия этого документа будет *«Справки\\»конфигурация» (archig)\\\\«арка»* |
| *Папка конфигурации* | Там может быть только три папки: *Отожоблик*, *Розничная торговля* и *CommonConfiguration*. Авторы SDK могут размещать свои файлы в *CommonConfiguration,* если следует использовать один и тот же набор файлов SDK, независимо от конфигурации, на которую нацелится потребитель SDK. |
| *Папка архитектуры* | Любая поддерживаемая папка *архитектуры* может существовать. Visual Studio поддерживает следующие архитектуры: x86, x64, ARM и нейтральные. Примечание: Win32 карты на x86, и AnyCPU карты нейтральным.<br /><br /> MSBuild выглядит только под *«CommonConfiguration» нейтральным* для платформы SDK. |
| *SDKManifest.xml* | В этом файле описывается, как Visual Studio должна потреблять SDK. Посмотрите на SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)]Манифест для:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Значение, отображаемые браузером объекта в списке просмотра.<br /><br /> **ПлатформаИдентичность:** Существование этого атрибута говорит Visual Studio и MSBuild, что SDK является платформой SDK и что ссылки, добавленные с него, не должны быть скопированы локально.<br /><br /> **TargetFramework:** Этот атрибут используется Visual Studio для обеспечения того, чтобы только проекты, ориентированные на те же рамки, указанные в значении этого атрибута, могли потреблять SDK.<br /><br /> **MinVSVersion:** Этот атрибут используется Visual Studio для потребления только SDK, которые применяются к нему.<br /><br /> **Справка:** Этот атрибут должен быть указан только для тех ссылок, которые содержат элементы управления. Информацию о том, содержит ли ссылка элементы управления, можно узнать ниже. |

## <a name="extension-sdks"></a>Пакеты SDK расширения

В следующих разделах описано, что нужно сделать для развертывания SDK расширения.

### <a name="installation"></a>Установка

Расширение SDK может быть установлено для конкретного пользователя или для всех пользователей без указания ключа реестра. Для установки SDK для всех пользователей используйте следующий путь:

*%Файлы программы% »Microsoft\<SDKs целевая платформа,\><номер\>версии платформы »ExtensionSDKs*

Для установки, конкретной для пользователя, используйте следующий путь:

*%USERPROFILE%-AppData-Local-Microsoft SDKs\<\>целевая платформа\>,v<номер версии платформы*

Если вы хотите использовать другое место, вы должны сделать одну из двух вещей:

1. Укажите его в ключе реестра:

     **\<HKLM-Software-Microsoft SDKs целевая платформа><\>номер версии\<платформы »Расширения SDKname>\<SDKversion>**\

     и добавить (по умолчанию) подключку, которая имеет значение `<path to SDK><SDKName><SDKVersion>`.

2. Добавьте свойство `SDKReferenceDirectoryRoot` MSBuild в файл проекта. Значение этого свойства представляет собой список делимитированных каталогов запятой, в которых находятся SDK расширения, на которые вы хотите ссылаться.

### <a name="installation-layout"></a>Планировка установки

У длиннее SDK есть следующая планировка установки:

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

1. \\<SDKName\> \\<SDKVersion:\>имя и версия расширения SDK происходит от соответствующих имен папок на пути к корню SDK. MSBuild использует эту идентификацию для поиска SDK на диске, и Visual Studio отображает эту идентичность в окне **свойства** и **диалоге справочного менеджера.**

2. *Папка ссылок:* файлы, содержащие AA. Это могут быть файлы или сборки Windows Metadata (WinMD).

3. *Папка Redist:* файлы, необходимые для отправления/отладки выполнения и должны быть упакованы как часть приложения пользователя. Все двоичные файлы должны быть помещены под *«redist\\<конфигурации\> \\ \><арки,* и двоичные имена должны иметь следующий формат, чтобы обеспечить уникальность: *]*\<»> компании. \<продукт>. \<цель>. \<расширение><em>. Например, «Microsoft.Cpp.Build.dll</em>. Все файлы с именами, которые могут столкнуться с именами файлов из других SDK (например, javascript, css, pri, xaml, png и jpg файлы) должны быть помещены под <em>\\ sredist\> \\<конфи<\> \\ арки<sdkname,\> \* за исключением файлов, которые связаны с элементами управления XAML. Эти файлы должны быть помещены\\ под «редистской<конфигурации\> \\<арки\> \\<-компонента.\></em>

4. *Папка DesignTime:* файлы, которые необходимы только в предварительное время/отладке и не должны быть упакованы как часть приложения пользователя. Это могут быть документы XML, библиотеки, заголовки, бинарные файлы для проектирования инструментов, артефакты MSBuild и так далее. Любой SDK, предназначенный для потребления народным проектом, должен иметь файл *SDKName.props.* Ниже показан образец этого типа файла.

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

    Ссылки на XML размещаются рядом с справочным файлом. Например, справочный документ XML для *«Ссылки\\<конфикаются\> \\<\>арки »sample.dll* сборки является *«Справки\\<конфигурации\> \\<арки\>ssample.xml*, и локализованная версия этого документа является *«Справки\\<config\> \\<арки\> \\<locale\>ssample.xml.*

5. *Папка конфигурации:* три субфалеры: *Отек,* *Розничная торговля*и *CommonConfiguration*. Авторы SDK могут размещать свои файлы в *CommonConfiguration,* когда следует использовать один и тот же набор файлов SDK, независимо от конфигурации, на которую нацелен потребитель SDK.

6. *Архитектурная* папка: поддерживаются следующие архитектуры: x86, x64, ARM, нейтральный. Win32 карты на x86, и AnyCPU карты нейтральным.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Файл *SDKManifest.xml* описывает, как Visual Studio должна потреблять SDK. Ниже представлен пример такого кода:

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

В следующем списке приведены элементы файла:

1. DisplayName: значение, которое отображается в справочном менеджере, исследователе решений, объектном браузере и других местах в пользовательском интерфейсе для Visual Studio.

2. Имя семьи продуктов: общее название продукта SDK. Например, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK называется "Microsoft.WinJS.1.0" и "Microsoft.WinJS.2.0", которые принадлежат к тому же семейством продуктов SDK, "Microsoft.WinJS". Этот атрибут позволяет Visual Studio и MSBuild сделать это соединение. Если этого атрибута не существует, имя SDK используется в качестве фамилии продукта.

3. FrameworkIdentity: определяет зависимость от одной или нескольких библиотек компонентов Windows. Значение этого атрибута ввозится в манифест приложения-потребителя. Этот атрибут применим только к библиотекам компонентов Windows.

4. TargetFramework: Определяет SDK, доступные в справочном менеджере и наборе инструментов. Это список целевых рамочных кликеров, например:.NET Framework, version -v2.0; .NET Framework, version-v4.5.1" Если указано несколько версий одной и той же целевой платформы, диспетчер ссылок использует самую низкую заданную версию для целей фильтрации. Например, если ".NET Framework, version'v2.0; .NET Framework, version'v4.5.1" указан, диспетчер референтов будет использовать ".NET Framework, version'v2.0". Если указан определенный целевой профиль фреймворка, только этот профиль будет использоваться диспетчером ссылок для целей фильтрации. Например, когда указана "Silverlight, version'v4.0, профиль -WindowsPhone", Reference Manager фильтрует только профиль Windows Phone; проект, ориентированный на полную рамку Silverlight 4.0, не видит SDK в справочном менеджере.

5. MinVSVersion: Минимальная версия Visual Studio.

6. MaxPlatformVerson: Максимальная версия целевой платформы должна использоваться для указания версий платформы, на которых не будет работать ваш Extension SDK. Например, на пакет Runtime-time microsoft Visual C's v11.0 следует ссылаться только на проекты Windows 8. Таким образом, MaxPlatformVersion проекта Windows 8 составляет 8,0. Это означает, что справочный менеджер отфильтровывает пакет Runtime Microsoft Visual C' для проекта [!INCLUDE[win81](../debugger/includes/win81_md.md)] Windows 8.1, и MSBuild бросает ошибку, когда проект ссылается на нее. Примечание: этот элемент поддерживается начиная [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]с .

7. ПрименяетсяДля: определяет SDK, доступные в справочном менеджере, определяя применимые типы проектов Visual Studio. Признаются девять значений: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed и Native. Автор SDK может использовать и ("я"), или ("&#124;"), а не ("!") операторам точно указать объем типов проектов, применимых к SDK.

    WindowsAppContainer определяет проекты для [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.

8. SupportPrefer32Bit: Поддерживаемые значения являются "истинными" и "ложными". По умолчанию является "Правда". Если значение настроено на "False", MSBuild [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] возвращает ошибку для проектов (или предупреждение для настольных проектов), если проект, который ссылается на SDK имеет Prefer32Bit включен. Для получения дополнительной информации о Prefer32Bit, [см. Страница Сборка, Проект Дизайнер (C)](../ide/reference/build-page-project-designer-csharp.md) или [Страница Компиляция, Конструктор проекта (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. ПоддерживаемыеАрхитектуры: список разграничения запятой архитектур, поддерживаемых SDK. MSBuild отображает предупреждение, если целевая архитектура SDK в проекте потребления не поддерживается. Если этот атрибут не указан, MSBuild никогда не отображает этот тип предупреждения.

10. ПоддерживаетMultipleVersions: Если этот атрибут настроен на **ошибку** или **предупреждение,** MSBuild указывает, что один и тот же проект не может ссылаться на несколько версий одного и того же семейства SDK. Если этот атрибут не существует или установлен для того чтобы **разрешить,** MSBuild не показывает этот тип ошибки или предупреждения.

11. AppX: Определяет путь к пакетам приложений для библиотеки компонентов Windows на диске. Это значение передается компоненту регистрации библиотеки компонентов Windows во время локальной отладки. Конвенция именования для названия * \<файла — компания\<>.> продукта. \<Архитектурная>. \<Конфигурация>. Версия \<>.appx*. Конфигурация и архитектура неявляются в имени атрибута и значении атрибута, если они не применяются к библиотеке компонентов Windows. Это значение применимо только к библиотекам компонентов Windows.

12. CopyRedistToSubDirectory: Определяет, где файлы под папкой *«Redist»* должны быть скопированы относительно корня пакета приложений (т.е. **месторасположения пакета,** выбранного в мастере **пакета создания** приложения) и корня макета времени выполнения. Местоположение по умолчанию является корнем пакета приложений и макета **F5.**

13. Зависит от: Список идентификаторов SDK, определяющих SDK, от которых зависит этот SDK. Этот атрибут отображается в панели деталей справочного менеджера.

14. MoreInfo: URL на веб-страницу, которая предоставляет помощь и более подробную информацию. Это значение используется в ссылке «Более подробная информация» в правом стеле справочного менеджера.

15. Тип регистрации: Определяет регистрацию WinMD в манифесте приложения и требуется для родного WinMD, который имеет аналог реализации DLL.

16. Справка по файлам: Указана только для тех ссылок, которые содержат элементы управления или являются родными WinMDs. Для получения информации о том, содержит ли ссылка элементы управления, [см.](#ToolboxItems)

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Указать местоположение элементов инструментария

Элемент **ToolBoxItems** схемы *SDKManifest.xml* определяет категорию и расположение элементов инструментария как в sDK платформы, так и в расширенном SDK. Ниже приведены приведения, как указать различные местоположения. Это применимо к ссылкам WinMD или DLL.

1. Разместите элементы управления в категории по умолчанию.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Место управления под определенным названием категории.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Место управления под определенными именами категорий.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Размещайте элементы управления под разными названиями категорий в Blend и Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Перечислите конкретные элементы управления по-разному в Blend и Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Перечислите конкретные элементы управления и поместите их под Общим пути Visual Studio или только в группе All Controls Group.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Перечислите конкретные элементы управления и отображайте только определенный набор в SelectItems, не находясь в наборе инструментов.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>См. также

- [Прохождение: Создание SDK с помощью СЗЗ](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Прохождение: Создание SDK с использованием C или Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)
