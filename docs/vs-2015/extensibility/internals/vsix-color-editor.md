---
title: Редактор цветов VSIX | Документация Майкрософт
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe8e54876f5b2ab3eda5c1bd8d35f0b0d0c788b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197243"
---
# <a name="vsix-color-editor"></a>Редактор цветов VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Средство редактор цветов расширений Visual Studio можно создавать и изменять собственные цвета для Visual Studio. Средство также можно создавать ключи ресурсов темы, чтобы цвета, которые можно использовать в коде. Это средство полезно для создания цвета для расширения Visual Studio, который поддерживает темы. Это средство позволяет открывать .pkgdef и XML-файлы. Тем Visual Studio (.vstheme файлы) можно использовать редактор Visual Studio расширение цвета, изменив расширение на .xml. Кроме того файлы .vstheme можно импортировать в текущий XML-файл.  
  
 ![Hero редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Hero редактора цветов VSIX")  
  
 **Файлы определений пакетов**  
  
 Определение (.pkgdef) файлы пакета находятся файлы, определяющие темы. Цвета, сами хранятся в темы цвета XML-файлов, которые компилируются в pkgdef-файл. Файлах pkgdef развертывания в Visual Studio для поиска расположения, обработано во время выполнения и объединяются для определения темы.  
  
 **Токены цветов**  
  
 Токен цвета состоит из четырех элементов:  
  
- **Имя категории:** Логическое группирование для набор цветов. Используйте существующее имя категории, если уже есть цвета, характерные для нужного элемента пользовательского интерфейса, или группы элементов пользовательского интерфейса.  
  
- **Имя токена:** Задает описательное имя для цвета токена и токена. Наборы включают фона и имена токенов передний план (текст), а также все их состояния, и эти должна называться, так как это легко определить пары и состояния, которые они применяются к.  
  
- **Значения цветов (или тона):** Требуется для каждой цветной темы. Всегда создавайте фона и текста цветовых значений в парах. Цвета сопоставляются для фона и цвета переднего плана, чтобы цвет текста (основной) всегда читается цвете фона, на котором он отрисовывается. Эти цвета связаны и будет использоваться совместно в пользовательском Интерфейсе. Если фон не предназначен для использования с текстом, не определяет цвет переднего плана.  
  
- **Имя цвета системы:** Для использования при отображении высокой контрастности.  
  
## <a name="how-to-use-the-tool"></a>Как использовать средство  
 Насколько возможно и уместно, следует повторно использовать существующие цвета Visual Studio вместо того, чтобы новые. Тем не менее для случаев, где определены соответствующие цветов, пользовательских цветов должны создаваться для сохранения темы расширения совместимы.  
  
 **Создание новых цвет маркеров**  
  
 Для создания настраиваемых цветов, с помощью редактора цвета расширения Visual Studio, выполните следующие действия.  
  
1. Чтобы Определите категории и маркер имена новые токены цветов.  
  
2. Выберите оттенки элемент пользовательского интерфейса, используемых для каждой темы и системный цвет для режима высокой контрастности.  
  
3. Редактор цвета для создания новых цвет маркеров.  
  
4. Используйте цвета в расширении Visual Studio.  
  
5. Протестируйте изменения в Visual Studio.  
  
   **Шаг 1. Чтобы Определите категории и маркер имена новые токены цветов.**  
  
   Предпочтительный именования для схемы для VSColor **[категория] [тип пользовательского интерфейса] [Состояние]** . Не используйте слово «цвет» в именах VSColor, так как он является избыточным.  
  
   Имена категорий обеспечивают логическое объединение и должен быть определен как узко максимально. Например имя окна единое средство может быть имя категории, но имя группы подразделение или проект весь бизнес целиком не. Группирование записей на категории помогает избежать путаницы между цветами с тем же именем.  
  
   Имя токена четко необходимо указать тип элемента и ситуациях или «состояние», для которого будет применяться цвет. Например, активные данные всплывающей подсказки **[тип пользовательского интерфейса]** может называться "**подсказке по данным**" и **[Состояние]** может называться "**Active**,» в результате чего имя цвета "**DataTipActive**.» Поскольку подсказок по данным текста, цвет фона и переднего плана должны быть определены. С помощью связывания фона и цвета переднего плана, редактора цвета автоматически создаст цвета "**DataTipActive**" для фона и "**DataTipActiveText**" переднего плана.  
  
   Если часть пользовательского интерфейса, имеет только одно состояние, **[Состояние]** можно опустить часть имени. Например, если нет изменений состояния, который может повлиять на цвет границы поля поиска имеет границу, затем имя токен цвета границы можно просто вызывать "**SearchBoxBorder**.»  
  
   Некоторые распространенные названия штатов включают:  
  
- Активная  
  
- Неактивно  
  
- MouseOver  
  
- MouseDown  
  
- Selected  
  
- Focused  
  
  Ниже приведены несколько имена токенов для частей элемента управления списка:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **Шаг 2. Выберите оттенки элемент пользовательского интерфейса, используемых для каждой темы и системный цвет для режима высокой контрастности.**  
  
  При выборе пользовательских цветов для пользовательского интерфейса, выберите аналогичные существующего элемента пользовательского интерфейса и использовать его цвета в качестве основы. Цвета для элементов пользовательского интерфейса in-box претерпели исследовании и проверке, поэтому они будут выглядеть соответствующий и правильную работу во всех темах.  
  
  **Шаг 3. Редактор цвета для создания новых цвет маркеров.**  
  
  Запуск редактора цвета и откройте или создайте новый XML-файл настраиваемой темы цвета. Выберите **изменить > новый цвет** в меню. Откроется диалоговое окно для указания категории и одно или несколько имен для записей цветов в этой категории.  
  
  ![Новый цвет редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "новый цвет редактора цветов VSIX")  
  
  Выберите существующую категорию или **новой категории** для создания новой категории. Откроется другое диалоговое окно создания нового имени категории:  
  
  ![Новая категория редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "новая категория редактора цветов VSIX")  
  
  Затем станет доступной в новой категории **новый цвет** категории выберите в раскрывающемся меню. После выбора категории, введите одному имени в строке для каждого нового цвета токена и выберите «Создать», после завершения:  
  
  ![Новый цвет редактора цветов VSIX заполнены](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "новый цвет редактора цветов VSIX заполнения")  
  
  Значение цвета обозначаются парами фона и цвета переднего плана, «None», указывающее на то, что цвет не был определен. Примечание: Если цвет не содержит текстового пара цветов цвет и фона, затем только фон необходимо определить.  
  
  ![Значения цветов редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "значения цвета редактора цветов VSIX")  
  
  Чтобы изменить токен цвета, выберите запись цвет из темы (столбец) этого токена. Добавьте значение цвета, либо ввести значение цвет с шестнадцатеричным значением в формате ARGB из 8 цифр, введя имени системного цвета в ячейку или с помощью раскрывающегося меню выберите нужный цвет с помощью набора шкалы или список системных цветов.  
  
  ![Редактор цветов VSIX — изменение цвета](../../extensibility/internals/media/vsix-color-editor-edit-color.png "редактора цветов VSIX — изменение цвета")  
  
  ![Фон редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "фон редактора цветов VSIX")  
  
  Для компонентов, которые не обязательно для отображения текста, введите значение только один цвет: цвет фона. В противном случае введите значения для цвета фона и текста, разделенных косой чертой.  
  
  При вводе значений режима высокой контрастности, введите допустимые имена цветов системы Windows. Не вводите жестко заданные значения ARGB. Список названий цветов допустимыми системными можно просмотреть, выбрав «фона: Система» или «переднего плана: Система» из раскрывающихся меню значение цвета. При создании элементов, которые имеют компонентов текста, используйте пары цвет фона или текста системы или текст могут стать нечитаемыми.  
  
  Завершив создание, Настройка и редактирование токены цветов, сохраните их в нужный XML или формат .pkgdef. Цвет маркеров ни на фоне, ни набор переднего плана будет сохранен как пустой цвета в формате XML, но удаляются в формате .pkgdef. Диалоговое окно предупредит вас потенциальной потери цвет, при попытке сохранить пустой цвета в pkgdef-файл.  
  
  **Шаг 4. Используйте цвета в расширении Visual Studio.**  
  
  После определения нового цвета маркеры, включают .pkgdef в файле проекта с помощью «Действие сборки» значение «Content» и «Включить в VSIX» значение «True».  
  
  ![Редактор цветов VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef редактор цветов VSIX")  
  
  В редакторе Visual Studio расширение цвета, выберите Файл > Просмотр кода ресурсов для просмотра кода, который используется для доступа к пользовательского цвета в пользовательском Интерфейсе на основе WPF.  
  
  ![Средство просмотра кода ресурсов редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "средство просмотра кода ресурсов редактора цветов VSIX")  
  
  Включить такой код в статическом классе в проекте. Ссылку на **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** должен быть добавлен в проект для использования **ThemeResourceKey** типа.  
  
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
  
 Это позволяет доступ к цвета в коде XAML и пользовательского интерфейса реагировать на изменения темы.  
  
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
  
 **Шаг 5. Протестируйте изменения в Visual Studio.**  
  
 Редактора цвета можно временно применить цвет маркеров для запущенных экземпляров Visual Studio для просмотра динамической изменения цветов без повторной сборки пакета расширения. Чтобы сделать это, нажмите кнопку «Применить эту тему к работающим окнам Visual Studio», расположенную в заголовке каждого столбца темы. Этот временный темы исчезнут после закрытия редактор цветов VSIX.  
  
 ![Применение редактора цветов VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "применение редактора цветов VSIX")  
  
 Для внесения постоянных изменений, повторно создавать и развертывать в расширение Visual Studio после добавления новых цветов в pkgdef-файл и написания кода, который будет использовать эти цвета. Перестроение в расширение Visual Studio объединит значения реестра для нового цвета в остальные темы. А затем снова откройте Visual Studio, открыть пользовательский Интерфейс и убедитесь, что новые цвета отображаются должным образом.  
  
## <a name="notes"></a>Примечания  
 Этот инструмент предназначен для использования для создания пользовательских цветов для уже существующих тем Visual Studio, или для изменения цвета пользовательскую тему Visual Studio. Чтобы создать полный пользовательские темы Visual Studio, загрузите [редактор цветовых тем Visual Studio расширение](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b) из коллекции расширений Visual Studio.  
  
## <a name="sample-output"></a>Пример результатов выполнения  
 **Выходные данные XML цвет**  
  
 XML-файл, созданный инструментом будет примерно следующим:  
  
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
  
 **Выходной цвет PKGDEF**  
  
 Файл pkgdef, созданные с помощью средства будет примерно следующим:  
  
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
  
 **Оболочки ключи ресурсов C#**  
  
 Цветовые ключи ресурсов, созданные с помощью средства будет примерно следующим:  
  
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
  
 **Оболочки словаря ресурсов WPF**  
  
 Цвет **ResourceDictionary** ключи, созданные с помощью средства будут примерно так:  
  
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
