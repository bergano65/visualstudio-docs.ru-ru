---
title: Define a profile to extend UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bdb6620f8d73bf7fae7b7dbb1b92af38e71345b6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295670"
---
# <a name="define-a-profile-to-extend-uml"></a>Определение профиля для расширения UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

You can define a *UML profile* to customize the standard model elements for specific purposes. A profile defines one or more *UML stereotypes*. Стереотип можно использовать, чтобы пометить тип как представляющий определенный вид объекта. Стереотип также может расширять список свойств элемента.

 В поддерживаемых выпусках Visual Studio установлено несколько профилей. Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). For more information about those profiles and about how to apply stereotypes, see [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 Вы можете определить собственные профили, чтобы адаптировать и расширить UML в соответствии с конкретной сферой бизнеса и архитектурой системы. Пример:

- Если вы регулярно определяете веб-сайты, можно определить собственный профиль, предоставляющий стереотип "Веб-страница", который можно применять к классам на схеме классов. Затем схемы классов можно использовать для планирования веб-сайта. Каждый класс "Веб-страница" будет иметь дополнительные свойства для содержимого страницы, стиля и т. д.

- При разработке программного обеспечения для банковских операций можно определить профиль, предоставляющий стереотип "Счет". Затем схемы классов можно использовать для определения различных типов счетов и отображения отношений между ними.

  Профили можно распределить между членами команды. Каждый член команды может установить ваш профиль. Это позволяет им редактировать и создавать модели, использующие стереотипы профиля.

> [!NOTE]
> Если стереотипы профиля применяются в редактируемой модели, после чего общий доступ к модели предоставляется другим людям, им необходимо установить тот же профиль на своих компьютерах. В противном случае они не смогут увидеть использованные стереотипы.

 A profile is often part of a larger [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] extension. Например, можно определить команду, которая переводит некоторые части модели в код. Вы можете определить профиль, который пользователи должны применять к пакетам, которые нужно перевести. Созданная команда распространяется вместе с профилем в одном расширении [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 Также можно определить локализованные варианты профиля. Пользователи, загружающие расширение, видят вариант, соответствующий их языку и региональным параметрам.

## <a name="DefineProfile"></a> How to Define a Profile

#### <a name="to-define-a-uml-profile"></a>Определение профиля UML

1. Создайте XML-файл с расширением `.profile`.

2. Add stereotype definitions according to the guidelines described in [The Structure of a Profile](#Schema).

3. Добавьте профиль в расширение Visual Studio (файл `.vsix`). Вы можете либо создать новое расширение для профиля, либо добавить профиль в существующее расширение.

     See the next section, [How to Add a Profile to a Visual Studio Extension](#AddProfile).

4. Установите расширение на компьютер.

    1. Дважды щелкните файл расширения, который имеет расширение `.vsix`.

    2. Перезапустите Visual Studio.

5. Убедитесь в том, что профиль установлен.

    1. Выберите модель в обозревателе UML.

    2. In the Properties window, click the **Profiles** property. Профиль появится в меню. Установите флажок рядом с профилем.

    3. Выберите элемент, для которого профиль определяет стереотипы. In the Properties window, click the **Stereotypes** property. Стереотипы появятся в списке. Установите флажок рядом с одним из стереотипов.

    4. Если профиль определяет дополнительные свойства для этого стереотипа, для их просмотра разверните свойство стереотипа.

6. Отправьте файл расширения другим пользователям [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для установки на их компьютеры.

## <a name="AddProfile"></a> How to Add a Profile to a Visual Studio Extension
 Чтобы установить профиль и разрешить его отправку другим пользователям, нужно добавить профиль в расширение Visual Studio. For more information, see [Deploying Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160780).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Определение профиля в новом расширении Visual Studio

1. Создайте проект расширения Visual Studio.

   > [!NOTE]
   > Чтобы выполнить эту процедуру, нужно установить пакет SDK для [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

   1. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

   2. In the **New Project** dialog box, under **Installed Templates**, expand **Visual C#** , click **Extensibility**, and then click **VSIX project**. Set the project name and click **OK**.

2. Добавьте профиль в проект.

   - In Solution Explorer, right-click the project, point to **Add**, and then click **Existing Item**. В диалоговом окне найдите файл профиля.

3. Set the profile file's **Copy to Output** property.

   1. In Solution Explorer, right-click the profile file, and then click **Properties**.

   2. In the Properties window, set the **Copy to Output Directory** property to **Copy Always**.

4. В обозревателе решений откройте файл `source.extension.vsixmanifest`.

    Файл откроется в редакторе манифеста расширения.

5. On the **Assets** page, add a row describing the profile:

   - Щелкните **Создать**. Set the fields in the **Add New Asset** dialog as follows.

   - Set **Type** to `Microsoft.VisualStudio.UmlProfile`

        Это значение недоступно в раскрывающемся списке. Введите его с клавиатуры.

   - Click **File on filesystem** and select the name of your profile file, for example `MyProfile.profile`

6. Выполните построение проекта.

7. **To debug the profile**, press F5.

    Откроется экспериментальный экземпляр Visual Studio. Откройте в нем проект моделирования. В обозревателе UML выберите корневой элемент модели, а затем в окне "Свойства" выберите свой профиль. Затем выберите элементы внутри модели и задайте стереотипы, определенные для них.

8. **To extract the VSIX for deployment**

   1. In Windows Explorer, open the folder **.\bin\Debug** or **.\bin\Release** to find the **.vsix** file. Это файл расширения [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Его можно установить на своем компьютере и отправить другим пользователям Visual Studio.

   2. Чтобы установить расширение, выполните указанные ниже действия.

       1. Дважды щелкните файл `.vsix`. Запустится установщик расширения Visual Studio.

       2. Перезапустите все выполняемые экземпляры Visual Studio.

   Если пакет [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] не установлен, для небольших расширений можно использовать описанную ниже альтернативную процедуру.

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Определение расширения профиля без использования Visual Studio SDK

1. Создайте каталог Windows, содержащий следующие три файла:

    - *YourProfile* `.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml` — введите это имя, как показано здесь, заключив его в квадратные скобки.

2. Измените файл `[Content_Types].xml`, включив в него приведенный ниже текст. Обратите внимание, что он содержит запись для каждого расширения имени файла.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Скопируйте существующий файл `extension.vsixmanifest` и измените его с помощью редактора XML. Измените узлы ID, Name и Content.

    - Пример файла `extension.vsixmanifest` можно найти в следующем каталоге:

         *drive* **:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - Узел Content должен иметь следующий вид:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Упакуйте три файла в сжатый ZIP-файл.

     In Windows Explorer, select the three files, right-click, point to **Send To**, and then click **Compressed (zipped) folder**.

5. Переименуйте ZIP-файл и измените его расширение с `.zip` на `.vsix`.

6. Чтобы установить профиль на любой компьютер с соответствующими выпусками Visual Studio, дважды щелкните файл `.vsix`.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Установка профиля UML из расширения Visual Studio

1. Дважды щелкните файл `.vsix` в проводнике или откройте его в Visual Studio.

2. Click **Install** in the dialog box that appears.

3. To uninstall or temporarily disable the extension, open **Extensions and Updates** from the **Tools** menu.

## <a name="Localized"></a> How to Define Localized Profiles
 Вы можете определить разные профили для разных языков и региональных параметров и упаковать их в одно расширение. При загрузке расширения пользователь увидит профиль, определенный для его языка и региональных параметров.

 Всегда нужно указывать профиль по умолчанию. Он отображается, если профиль для языка и региональных параметров пользователя не определен.

#### <a name="to-define-a-localized-profile"></a>Определение локализованного профиля

1. Create a profile as described in the previous sections[How to Define a Profile](#DefineProfile) and [How to Add a Profile to a Visual Studio Extension](#AddProfile). Это профиль по умолчанию, который будет использоваться в любой установке, для которой не предоставлен локализованный профиль.

2. Добавьте новый каталог в каталог, в котором уже находится файл профиля по умолчанию.

    > [!NOTE]
    > Если расширение создается с помощью проекта расширения Visual Studio, для добавления новой папки в проект используйте обозреватель решений.

3. Измените имя нового каталога на короткий код ISO для языка локализации, например `bg` для болгарского или `fr` для французского. Следует использовать нейтральный идентификатор языка и региональных параметров (как правило, состоящий из двух букв), а не указывать конкретные язык и региональные параметры, например `fr-CA`. For more information about culture codes, see [CultureInfo.GetCultures method](https://go.microsoft.com/fwlink/?LinkId=160782), which provides a complete list of culture codes.

4. Добавьте копию профиля по умолчанию в новый каталог. Не изменяйте имя файла.

     A sample [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Extension folder, before it is built or compressed into a `.vsix` file, would contain the following folders and files:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Не следует вставлять в файл `extension.vsixmanifest` ссылку на локализованные версии профилей. Скопированные файлы профилей должны иметь те же имена, что и профили в родительской папке.

5. Измените новую копию профиля, переведя на соответствующий язык все части, которые будут видны пользователю, такие как атрибуты `displayName`.

6. Вы можете создать дополнительные папки и локализованные профили для неограниченного числа языков и региональных параметров.

7. Выполните сборку расширения Visual Studio, создав проект расширения или сжав все файлы, следуя инструкциям в предыдущих разделах.

## <a name="Schema"></a> The Structure of a Profile
 The XSD file for UML profiles can be found in the following sample: [Setting Stereotypes and Profiles XSD](https://go.microsoft.com/fwlink/?LinkID=213811). Для облегчения изменения файлов профилей установите файл `.xsd` в следующий каталог:

 **%ProgramFiles%\Microsoft Visual Studio [version]\Xml\Schemas**

 В этом разделе в качестве примера используется профиль C#. Полное определение профиля можно найти в следующем каталоге:

 *drive* **:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**

 В вашей установке первые части этого пути могут отличаться от указанных.

 For more information about the .NET profile, see [Standard stereotypes for UML models](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>Основные разделы определения профиля UML
 Каждый профиль имеет следующее содержимое:

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> В атрибуте `name` не должно быть пробелов или знаков препинания. Атрибут `displayName`, отображаемый в пользовательском интерфейсе, должен представлять собой допустимую строку XML.

 В каждом профиле имеется три основных раздела. Ниже они представлены в обратном порядке.

- `<propertyTypes>` — список типов, которые используются для свойств, определенных в разделе стереотипов.

- `<metaclasses>` — список типов элементов модели, к которым применимы стереотипы в этом профиле, такие как IClass, IInterface, IOperation, IDependency.

- `<stereotypes>` — определения стереотипов. Каждое определение включает имена и типы свойств, добавляемых в целевой элемент модели.

#### <a name="property-types"></a>Типы свойств
 The `<propertyTypes>` section declares a list of types that are used for properties in the `<stereotypes>` section. Существует две разновидности типов свойств: внешние типы и перечисление.

 Внешний тип объявляет полное имя стандартного типа .NET.

```
<externalType name="System.String" />
```

 Тип перечисления определяет набор литеральных значений.

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>Метаклассы
 Раздел `<metaclasses>` представляет собой список типов элементов модели, для которых можно определить стереотипы в данном профиле.

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 For the full list of model element and relationship types that you can use as metaclasses, see [Model Element Types](#Elements).

#### <a name="stereotype-definition"></a>Определение стереотипа
 Раздел `<stereotypes>` содержит одно или несколько определений стереотипов.

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 В каждом стереотипе перечислены один или несколько типов элементов модели или отношений, к которым его можно применять. Можно указать имя базового типа, в который включены все производные типы. Например, если задать `Microsoft.VisualStudio.Uml.Classes.IType`, стереотип можно применить к `IClass`, `IInterface`, `IEnumeration` и некоторым другим типам элементов.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 Атрибут `name` объекта `metaclassMoniker` представляет собой ссылку на элемент в разделе `<metaClasses>`.

> [!NOTE]
> Имя моникера должно начинаться с `/yourProfileName/`, где `yourProfileName` определяется в атрибуте `name` профиля (CSharpProfile в этом примере). Моникер заканчивается именем одной из записей в разделе метаклассов.

 В каждом стереотипе можно перечислить сколько угодно свойств (или ни одного), которые он добавляет в любой элемент модели, к которому применяется. The `<propertyType>` contains a link to one of the types that are defined in the `<propertyTypes>` section. Это должна быть ссылка `<externalTypeMoniker>`, указывающая на `<externalType>,`, или `<enumerationTypeMoniker>`, указывающая на `<enumerationType>`. Ссылка начинается с имени профиля.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="Elements"></a> Model Element Types
 The set of types for which you can define stereotypes is listed in [UML model element types](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>Устранение неполадок
 Мои стереотипы не отображаются в моделях UML.
Необходимо выбрать свой профиль в пакете или модели. Стереотипы появятся в элементах внутри пакета или модели. For more information, see [Add stereotypes to UML model elements](../modeling/add-stereotypes-to-uml-model-elements.md).

 The following error appears when I open a UML model: **VS1707: The following profiles cannot be loaded because a serialization error occurred: MyProfile.profile**
1. Убедитесь в правильности базового синтаксиса XML файла PROFILE.

2. Убедитесь в том, что имя каждого моникера представлено в форме /имя_профиля/имя_узла. Имя_профиля — это значение атрибута имени в корневом узле профиля. Имя_узла — это значение атрибута имени в метаклассе, внешнем типе или типе перечисления.

3. Ensure the syntax is as described here, and as demonstrated in _drive_ **:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .

4. Удалите расширение с ошибкой. В меню **Сервис** выберите пункт **Расширения и обновления**.

   - Если расширение не отображается, см. следующий пункт.

5. Выполните повторную сборку файла VSIX и откройте его в проводнике для повторной установки. Перезапустите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   The extension does not appear in Extension Manager, but when you try to re-install it, the following message appears: **The extension is already installed to all applicable products.**
   1. Remove the extension file from a subfolder of *LocalAppData*\Microsoft\VisualStudio\\[version]\Extensions\

   - To see *LocalAppData*, you must set Show Hidden Files and Folders in the View tab of the Windows Explorer Folder Options.

   - *LocalAppData* is typically in C:\Users\\*userName*\AppData\Local\

6. Перезапустите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>См. также раздел
 [Add stereotypes to UML model elements](../modeling/add-stereotypes-to-uml-model-elements.md) [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Standard stereotypes for UML models](../modeling/standard-stereotypes-for-uml-models.md) [Sample: Color UML Elements by Stereotype](https://go.microsoft.com/fwlink/?LinkID=213841) [Sample: Setting Stereotypes, Profiles XSD](https://go.microsoft.com/fwlink/?LinkID=213811)
