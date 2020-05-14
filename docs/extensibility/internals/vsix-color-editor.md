---
title: VSIX Цветредактор (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704046"
---
# <a name="vsix-color-editor"></a>Редактор цветов VSIX
Инструмент visual Studio Extension Color Editor может создавать и редотировать пользовательские цвета для Visual Studio. Инструмент также может генерировать ключи ресурса темы, так что цвета могут быть использованы в коде. Этот инструмент полезен для создания цветов для расширения Visual Studio, который поддерживает тематику. Этот инструмент может открывать файлы .pkgdef и .xml. Темы Visual Studio (.vstheme файлы) могут быть использованы с редактором цвета расширения Visual Studio, изменив расширение файла на .xml. Кроме того, файлы .vstheme могут быть импортированы в текущий файл .xml.

 ![Редактор цветов VSIX — главный имиджевый баннер](../../extensibility/internals/media/vsix-color-editor-hero.png "Редактор цветов VSIX — главный имиджевый баннер")

 **Файлы определения пакета**

 Определение пакета (.pkgdef) файлы файлы, которые определяют темы. Сами цвета хранятся в файлах цвета темы .xml, которые компилируются в файл .pkgdef. Файлы .pkgdef развертываются в поисковых локациях Visual Studio, обрабатываются во время выполнения и объединяются для определения тем.

 **Цветовые токены**

 Цветной токен состоит из четырех элементов:

- **Название категории:** Логическая группировка для набора цветов. Используйте существующее имя категории, если уже есть цвета, характерные для желаемого элемента uI, или группа элементов uI.

- **Название токенов:** Описательное название для цветовых маркеров и наборов маркеров. Наборы включают имена маркеров фона и переднего плана (текста), а также все их состояния, и они должны быть названы таким образом, чтобы легко определить пары и состояния, к которым они применяются.

- **Цветовые значения (или оттенки):** Нужны для каждой цветной темы. Всегда создавайте значения фона и цвета текста парами. Цвета парируются для фона/переднего плана, так что цвет текста (переднего плана) всегда читается на фоне цвета, на котором он нарисован. Эти цвета связаны между собой и будут использоваться вместе в uI. Если фон не предназначен для использования с текстом, не определяйте цвет переднего плана.

- **Название цвета системы:** Для использования в высококонтрастных дисплеях.

## <a name="how-to-use-the-tool"></a>Как использовать инструмент
 Насколько это возможно, и где это уместно, существующие цвета Visual Studio должны быть повторно использованы, а не новые. Однако в тех случаях, когда не определены соответствующие цвета, следует создавать пользовательские цвета, чтобы сохранить совместимые с расширением их.

 **Создание новых цветовых токенов**

 Чтобы создать пользовательские цвета с помощью редактора Color Расширения Visual Studio, выполните следующие действия:

1. Определите категорию и имена маркеров для новых цветовых токенов.

2. Выберите оттенки, которые элемент uI будет использовать для каждой темы и цвет системы для high Contrast.

3. Используйте редактор цветов для создания новых цветовых токенов.

4. Используйте цвета в расширении Visual Studio.

5. Проверьте изменения в Visual Studio.

   **Шаг 1: Определите категорию и имена маркеров для новых цветовых токенов.**

   Предпочтительной схемой именования для VSColor является **«Категория» (тип UI) .** Не используйте слово «цвет» в названиях VSColor, так как оно является излишним.

   Названия категорий обеспечивают логические группировки и должны быть определены как можно более узко. Например, имя одного окна инструмента может быть названием категории, но имя всего бизнес-подразделения или проектной группы не является. Группировка записей в категории помогает предотвратить путаницу между цветами с тем же именем.

   Имя маркера должно четко указывать тип элемента и ситуации, или "состояние", для которого будет применен цвет. Например, тип **«UI»** активного наконечника данных может быть назван **«DataTip»,** а **«государство»** —**«Активный»,** в результате чего будет названо цветовое имя **«DataTipActive».** Поскольку советы по данным имеют текст, необходимо определить как передний план, так и цвет фона. Используя сопряжение фона/переднего плана, редактор цветов автоматически создает цвета «**DataTipActive**» для фона и «**DataTipActiveText**» для переднего плана.

   Если часть uI имеет только одно состояние, **часть** имени может быть опущена. Например, если в поле поиска есть граница и нет изменения состояния, которое повлияло бы на цвет границы, то название цветного маркера границы можно просто назвать **«SearchBoxBorder».**

   Некоторые общие названия состояний включают в себя:

- Активна

- Неактивный

- MouseOver

- Mousedown

- Выбрано

- Focused

  Примеры нескольких имен маркеров для частей элемента элемента списка:

- ListItem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemS выбран

- ListItemSизбраноГраница

- ListItemDisabled

- ListItemDisabledBorder

  **Шаг 2: Выберите оттенки, которые элемент uI будет использовать для каждой темы и цвет системы для high Contrast.**

  При выборе пользовательских цветов для пользовательского пользовательского иного пользовательского иного элемента пользовательского или ам-центра выберите аналогичный элемент пользовательского или амприсии и используйте его цвета в качестве основы. Цвета для элементов uI в коробке прошли обзор и тестирование, поэтому они будут выглядеть соответствующим образом и вести себя правильно во всех темах.

  **Шаг 3: Используйте цветной редактор для создания новых цветовых токенов.**

  Запустите редактор цветов и откройте или создайте новый пользовательский файл темы .xml. Выберите **edit > New Color** из меню. Это открывает диалог для указания категории и одного или нескольких имен для цветных записей в этой категории:

  ![Новый цвет редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Новый цвет редактора цветов VSIX")

  Выберите существующую категорию или выберите **новую категорию** для создания новой категории. Откроется другой диалог, создающий новое название категории:

  ![Новая категория редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "Новая категория редактора цветов VSIX")

  Новая категория затем станет доступна в новом **цвете** категории выпадающих меню. После выбора категории введите одно имя на строку для каждого нового цветного маркера и выберите "Создать" при завершении:

  ![Новый цвет заполнения редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Новый цвет заполнения редактора цветов VSIX")

  Значения цвета отображаются в парах фона/переднего плана, при этом "Нет" указывает на то, что цвет не определен. Примечание: если цвет не имеет цвет текста /фоновая цветовая пара, то необходимо определить только фон.

  ![Редактор цветов VSIX — значения цвета](../../extensibility/internals/media/vsix-color-editor-color-values.png "Редактор цветов VSIX — значения цвета")

  Чтобы отсеивать маркер цвета, выберите запись цвета для темы (колонки) этого маркера. Добавьте значение цвета, введя шестицветное значение в 8-значном формате ARGB, введя имя цвета системы в ячейку, или используя выпадающее меню, чтобы выбрать нужный цвет через набор цветных ползунок или список системных цветов.

  ![Редактор цветов VSIX — изменение цвета](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Редактор цветов VSIX — изменение цвета")

  ![Фон редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Фон редактора цветов VSIX")

  Для компонентов, которые не нуждаются в отображении текста, введите только одно цветовое значение: цвет фона. В противном случае введите значения как фонового, так и цвет текста, разделенные передний слэш.

  При вводе значений для High Contrast введите действительные цветные имена системы Windows. Не вводите жесткие значения ARGB. Вы можете просмотреть список действительных названий цвета системы, выбрав "Background: System" или "Foreground: System" из меню выпадения цветового значения. При создании элементов, которые имеют текстовые компоненты, используйте правильную цветовую пару фоновых/текстовых систем или текст может быть нечитаемым.

  Когда вы закончите создавать, настраивать и редактировать цветовые маркеры, сохраните их в желаемом формате .xml или .pkgdef. Цветовые токены без фона и набора передних мест будут сохранены как пустые цвета в формате .xml, но отбрасываются в формате .pkgdef. Диалог предупредит вас о возможной потере цвета, если вы попытаетесь сохранить пустые цвета в файле .pkgdef.

  **Шаг 4: Используйте цвета в расширении Visual Studio.**

  После определения новых цветовых токенов включите .pkgdef в файл проекта с набором "Build Action" на "Content" и "Включить в VSIX" набор "True".

  ![Редактор цветов VSIX — PKGDEF](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Редактор цветов VSIX — PKGDEF")

  В редакторе Color-Редактор расширения Visual Studio выберите Code > View Resource Code для просмотра кода, который используется для доступа к пользовательским цветам в пользовательском доступе на основе WPF.

  ![Редактор цветов VSIX — средство просмотра кода ресурса](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Редактор цветов VSIX — средство просмотра кода ресурса")

  Включите этот код в статический класс в проекте. Ссылка на **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** должен быть добавлен в проект, чтобы использовать тип **ThemeResourceKey.**

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Это позволяет получить доступ к цветам в коде XAML и позволяет uI реагировать на изменения темы.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Шаг 5: Проверьте изменения в Visual Studio.**

 Редактор цветовых цветов может временно применять цветные маркеры к запущенным экземплярам Visual Studio для просмотра живых изменений в цветах без восстановления пакета расширения. Для этого нажмите кнопку "Применить эту тему к запуску windows Visual Studio", расположенную на заголовке каждой тематиной колонки. Эта временная тема исчезнет, когда редактор Цветов VSIX будет закрыт.

 ![Применение редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "Применение редактора цветов VSIX")

 Чтобы сделать изменения постоянными, перестроить и передислоцировать расширение Visual Studio после добавления новых цветов в файл .pkgdef и написания кода, который будет использовать эти цвета. Восстановление расширения Visual Studio объединит значения реестра для новых цветов в остальные темы. Затем перезапустите Visual Studio, просмотрите uI и убедитесь, что новые цвета выглядят как ожидалось.

## <a name="notes"></a>Примечания
 Этот инструмент предназначен для создания пользовательских цветов для уже существующих тем Visual Studio, или для редактирования цветов пользовательской темы Visual Studio. Чтобы создать полную пользовательскую темы Visual Studio, загрузите [расширение редактора цветовой тематики Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) из галереи Визуальных расширений Studio.

## <a name="sample-output"></a>Пример выходных данных
 **Выход цвета XML**

 Файл .xml, генерируемый инструментом, будет аналогичен этому:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **Выход цвета PKGDEF**

 Файл .pkgdef, генерируемый инструментом, будет аналогичен этому:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Обертка ключей ресурса C**

 Ключи ресурса цвета, генерируемые инструментом, будут похожи на это:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **Обертка словаря ресурсов WPF**

 Цветные **клавиши ResourceDictionary,** генерируемые инструментом, будут похожи на это:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
