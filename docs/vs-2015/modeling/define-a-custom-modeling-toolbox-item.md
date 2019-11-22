---
title: Define a custom modeling toolbox item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac299f18e544ef4f3215707abbdc3d9e8d266de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299298"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Определение пользовательского элемента для панели элементов моделирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы упростить создание элемента или группы элементов по часто используемому шаблону, можно добавить на панель элементов схем моделирования в Visual Studio новые инструменты. Можно распространить эти элементы панели элементов другим пользователям Visual Studio.

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Пользовательский инструмент создает один или несколько новых элементов в схеме. Например, можно создать пользовательский инструмент, позволяющий создавать следующие элементы:

- Пакет, связанный с профилем .NET, и класс со стереотипом .NET.

- Пара классов, связанная ассоциацией для представления шаблона наблюдателя.

> [!NOTE]
> Этот метод можно использовать для создания инструментов элемента. Таким образом, можно создать инструменты, которые можно перетаскивать из панели элементов на схему. Инструменты соединителя создавать нельзя.

## <a name="DefineTool"></a> Defining a Custom Modeling Tool

#### <a name="to-define-a-custom-modeling-tool"></a>Порядок определения пользовательского инструмента моделирования

1. Создайте схему UML, которая содержит элемент или группу элементов.

    - Эти элементы могут иметь отношения между собой и дочерние элементы, например порты, атрибуты, операции или закрепления.

2. Сохраните схему, используя имя, которое хотите присвоить новому инструменту. On the **File** menu, use **Save…As**.

3. С помощью проводника Windows скопируйте два файла схемы в следующую папку или любую вложенную папку:

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom Toolbox Items**

    - Создайте эту папку, если она еще не существует. You might have to create both **Architecture Tools** and **Custom Toolbox Items**.

    - Copy both diagram files, one with a name that ends "…**diagram**" and the other with a name that ends "…**diagram.layout**"

    - Можно создать столько пользовательских инструментов, сколько необходимо. Используйте одну схему для каждого инструмента.

4. (Optional) Create a **.tbxinfo** file as described in [How to Define the Properties of Custom Tools](#tbxinfo), and add it to the same directory. Это позволяет определить значок панели элементов, подсказку и т. п.

    - A single **.tbxinfo** file can be used to define several tools. Он может ссылаться на файлы схемы, расположенные во вложенных папках.

5. Перезапустите Visual Studio. Дополнительные инструменты будут отображаться на панели элементов для соответствующего типа схемы.

### <a name="what-the-custom-tool-will-replicate"></a>Что именно реплицирует пользовательский инструмент
 Пользовательский инструмент реплицирует большинство функций исходной схемы:

- Имена При создании элемента с панели элементов в конец имени добавляется число, если требуется избежать дублирования имен в рамках одного пространства имен.

- Цвета, размеры и фигуры

- Стереотипы и профили пакета

- Значения свойств, таких как "Является абстрактным"

- Связанные рабочие элементы

- Кратности и другие свойства отношений

- Относительное положение фигур.

  Следующие функции не будут сохраняться в пользовательском инструменте:

- Простые фигуры Это фигуры, не связанные с элементами модели, которые можно рисовать на некоторых типах схем.

- Маршрутизация соединителей Если маршрутизация соединителей осуществляется вручную, она не сохраняется при использовании инструмента. Положения некоторых вложенных фигур, таких как порты, не сохраняется относительно своих владельцев.

## <a name="tbxinfo"></a> How to Define the Properties of Custom Tools
 A toolbox information ( **.tbxinfo**) file allows you to specify a toolbox name, icon, tooltip, tab, and help keyword for one or more custom tools. Give it any name, such as **MyTools.tbxinfo**.

 Общий вид файла выглядит следующим образом:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Значение каждого элемента может быть любым из следующих:

- Как показано в примере, `<bmp fileName="…"/>` для значка панели элементов и `<value>string</value>` для других элементов.

  \- или -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   В этом случае вы предоставляете скомпилированную сборку, в которой строковые значения были скомпилированы в качестве ресурсов.

  Добавьте узел `<customToolboxItem>` для каждого элемента панели элементов, который необходимо определить.

  The nodes in the **.tbxinfo** file are as follows. Для каждого узла имеется значение по умолчанию.

|Имя узла|Определяет следующее|
|---------------|-------------|
|displayName|Имя элемента панели элементов.|
|tabName|Вкладка панели элементов, на которой должен отображаться элемент. Можно указать либо имя обычной вкладки для этого типа схемы, либо отдельное имя.|
|изображение|The location of the bitmap ( **.bmp**) file, which must have height and width of 16, and a color depth of 24 bits.|
|f1Keyword|Ключевое слово, осуществляющее поиск раздела справки.|
|подсказка|Подсказка для этого инструмента.|

 Можно изменить файл точечного рисунка в Visual Studio и задать его высоту и ширину равными 16 в окне "Свойства".

> [!NOTE]
> Если начать использовать файл TBXINFO после проведения экспериментов по использованию отдельных файлов схем, может оказаться, что панель элементов содержит старые и новые версии элемента панели элементов. Это также может произойти, если имя файла схемы было неправильно указано в файле TBXINFO. If this occurs, on the shortcut menu of the toolbox choose **Reset Toolbox**. Настраиваемые элементы панели элементов исчезают. Перезапустите Visual Studio, после чего отображаются правильные пользовательские элементы.

## <a name="Extension"></a> How to Distribute Toolbox Items in a Visual Studio Extension
 You can distribute toolbox items to other [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] users by packaging them into a Visual Studio Extension (VSIX). Команды, профили и другие расширения можно упаковать в один файл VSIX. For more information, see [Deploying Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160780).

 Для создания расширения Visual Studio обычно используется шаблон проекта VSIX. Чтобы воспользоваться им, необходимо установить [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Добавление элемента панели элементов в расширение Visual Studio

1. [Create and test one or more custom tools](#DefineTool).

2. [Create a .tbxinfo file](#tbxinfo) that references the tools.

3. Создайте проект расширения Visual Studio.

     \- или -

     Определите новый проект расширения Visual Studio.

    1. В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.

    2. In the **New Project** dialog box, under **Installed Templates**, choose **Visual C#** , **Extensibility**, **VSIX project**.

4. Добавьте в проект определения панели элементов. Include the **.tbxinfo** file, the diagram files, bitmap files, and any resource files, and make sure that they are included in the VSIX.

    - In Solution Explorer, on the shortcut menu of the VSIX project, choose **Add**, **Existing Item**. In the dialog box, set **Objects of Type: All Files**. Locate the files, select them all, and then choose **Add**.

        > [!NOTE]
        > В этом проекте нельзя открыть файлы схемы в редакторе моделей.

5. Задайте следующие свойства всех недавно добавленных файлов. В то же время можно задавать их свойства, выбрав всех их в обозревателе решений. Не следует изменять свойства других файлов в проекте.

     **Copy to Output Directory** = **Copy Always**

     **Build Action** = **Content**

     **Include in VSIX** = **true**

6. Откройте **source.extension.vsixmanifest**. Открывается в редакторе манифеста расширения.

7. Under **Metadata**, add a description for the custom tools.

     Under **Assets**, choose **New** and then set the fields in the dialog as follows:

    - **Type** = **Custom Extension Type**

    - Тип = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Это значение не указано в раскрывающемся списке. Его необходимо ввести с помощью клавиатуры.

    - **Source** = **File on filesystem**.

    - **Path** = your **.tbxinfo** file, for example **MyTools.tbxinfo**

8. Выполните построение проекта.

9. **To verify that the extension works**, press F5. Откроется экспериментальный экземпляр Visual Studio.

     В экспериментальном экземпляре создайте или откройте схему UML соответствующего типа. Убедитесь, что новый инструмент отображается на панели элементов и что он правильно создает элементы.

10. **To obtain a VSIX file for deployment:** In Windows Explorer, open the folder **.\bin\Debug** or **.\bin\Release** to find the **.vsix** file. Это файл расширения [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Его можно установить на своем компьютере и отправить другим пользователям Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Установка пользовательских инструментов из расширения Visual Studio

1. Откройте файл `.vsix` в проводнике Windows или в Visual Studio.

2. Choose **Install** in the dialog box that appears.

3. To uninstall or temporarily disable the extension, open **Extensions and Updates** from the **Tools** menu.

## <a name="localization"></a>Локализация
 Можно создать расширение, которое при установке на другом компьютере отображает имена и подсказки для инструмента на языке целевого компьютера.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Предоставление версий инструмента на нескольких языках

1. Создайте проект расширения Visual Studio, который содержит один или несколько пользовательских инструментов.

    In the **.tbxinfo** file, use the resource file method to define the tool's `displayName`, toolbox `tabName`, and the tooltip. Создайте файл ресурсов, в котором определяются эти строки, скомпилируйте его в сборку, а затем сошлитесь на него из файла TBXINFO.

2. Создайте дополнительные сборки, содержащие файлы ресурсов со строками на других языках.

3. Поместите каждую дополнительную сборку в папку, имя которой является идентификатором соответствующего языка и региональных параметров. For example, place a French version of the assembly inside a folder that is named **fr**.

4. Следует использовать нейтральный идентификатор языка и региональных параметров (как правило, состоящий из двух букв), а не указывать конкретные язык и региональные параметры, например `fr-CA`. For more information about culture codes, see [CultureInfo.GetCultures method](https://go.microsoft.com/fwlink/?LinkId=160782), which provides a complete list of culture codes.

5. Выполните сборку расширения Visual Studio и распределите его.

6. Когда расширение установлено на другом компьютере, будет автоматически загружается версия файла ресурсов для языка и региональных параметров локального пользователя. Если вы не указали версию для языка и региональных параметров пользователя, будут использоваться ресурсы по умолчанию.

   Этот метод нельзя использовать для установки разных версий схемы прототипа. Имена элементов и соединителей будут одинаковыми во всех установках.

## <a name="other-toolbox-operations"></a>Другие операции панели элементов
 Обычно в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] панель элементов можно персонализировать, переименовывая инструменты, перемещая их на другие вкладки и удаляя их. Однако эти изменения не сохраняются для пользовательских инструментов моделирования, которые созданы с использованием процедур, описанных в этом разделе. При перезапуске [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] пользовательские инструменты отображаются с заданными для них именами и расположениями на панели элементов.

 Furthermore, your custom tools will disappear if you perform the **Reset Toolbox** command. Однако после перезапуска [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] они снова появляются.

## <a name="see-also"></a>См. также раздел
 [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Define a menu command on a modeling diagram](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md)
