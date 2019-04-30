---
title: Обзор объектной модели ленты
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83f906ad9e5ded349250fe5324076527975c9bf6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446992"
---
# <a name="ribbon-object-model-overview"></a>Обзор объектной модели ленты
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Предоставляет строго типизированную объектную модель, можно использовать для получения и задания свойств элементов управления ленты во время выполнения. Например можно динамически заполнения элементов управления меню, или отображать и скрывать элементы управления в зависимости от контекста. Можно также добавить вкладок, групп и элементов управления на ленту, но только до загрузки ленты в приложение Office. Сведения см. в разделе [задать свойства, которые становятся доступными только для чтения](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Эта объектная модель ленты состоит главным образом из [класс ленты](#RibbonClass), [ленте события](#RibbonEvents), и [классы элементов управления ленты](#RibbonControlClasses).

## <a name="RibbonClass"></a> Класс ленты
 При добавлении нового **Лента (визуальный конструктор)** элемента в проект Visual Studio добавляет **ленты** класс в проект. **Ленты** класс наследует от <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> класса.

 Этот класс отображается как разделяемый класс, распределенный между файл кода ленты и файл кода конструктора лент.

## <a name="RibbonEvents"></a> События ленты
 **Ленты** класс содержит следующие три события:

|событие|Описание|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Вызывается, когда приложение Office загружает настройки ленты. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Автоматически добавляется обработчик событий в файл кода ленты. Этот обработчик событий можно используйте для запуска пользовательского кода при загрузке ленты.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Позволяет кэшировать изображения в настройке ленты при загрузке ленты. Вы можете получить некоторого улучшения производительности при написании кода для кэширования изображений ленты в этом обработчике событий. Дополнительные сведения см. в разделе <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Возникает при закрытии экземпляра ленты.|

## <a name="RibbonControlClasses"></a> Элементы управления ленты
 <xref:Microsoft.Office.Tools.Ribbon> Пространство имен содержит типы для каждого элемента управления, которое будет отображаться в **элементы управления ленты Office** группе **элементов**.

 В следующей таблице показаны тип для каждого `Ribbon` элемента управления. Описание каждого элемента управления, см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

|Имя элемента управления|Имя класса|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Раскрывающийся список**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**Поле ввода "**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Коллекция**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Группа**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**TAB**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**Выключатель**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 <xref:Microsoft.Office.Tools.Ribbon> Пространства имен использует префикс «Ribbon» для этих типов, чтобы избежать конфликта имен с именами классов элементов управления в <xref:System.Windows.Forms> пространства имен.

 При добавлении элемента управления в конструктор ленты конструктор лент объявляет класс для этого элемента управления как поле в файле кода конструктора лент.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Типичных задач с помощью свойств элементов управления ленты
 Каждый `Ribbon` элемент управления содержит свойства, которые можно использовать для выполнения различных задач, таких как назначение метку к элементу управления или скрытие и отображение элементов управления.

 В некоторых случаях свойства становятся доступными только для чтения после загрузки ленты или после добавления элемента управления для динамического меню. Дополнительные сведения см. в разделе [задать свойства, которые становятся доступными только для чтения](#SettingReadOnlyProperties).

 В следующей таблице описаны некоторые задачи, которые можно выполнять с помощью `Ribbon` свойства элемента управления.

|Для выполнения этой задачи|Выполните следующее.|
|--------------------|--------------|
|Скрыть или отобразить элемент управления.|Свойство видимым.|
|Включает или отключает элемент управления.|Свойство Enabled.|
|Установите размер элемента управления.|Свойство ControlSize.|
|Получение изображения, отображаемого в элементе управления.|Свойство изображения.|
|Изменение метки элемента управления.|Свойство метки.|
|Добавление пользовательских данных в элемент управления.|Свойство Tag.|
|Получить элементы в <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, или<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> элемент управления.|Свойство элементов.|
|Добавить элементы в <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> элемента управления.|Свойство элементов.|
|Добавление элементов управления для <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Свойство элементов.<br /><br /> Добавлять элементы управления к <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> после загрузки ленты в приложение Office, необходимо задать <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> свойства **true** до загрузки ленты в приложение Office. Сведения см. в разделе [задать свойства, которые становятся доступными только для чтения](#SettingReadOnlyProperties).|
|Получение выбранного элемента из <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Свойство SelectedItem. Для <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, используйте <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> свойство.|
|Получить список групп <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Используйте свойство <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Укажите число строк и столбцов, которые отображаются в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Используйте <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> и <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> свойства.|

## <a name="SettingReadOnlyProperties"></a> Задать свойства, которые становятся доступными только для чтения
 Некоторые свойства можно задать только в том случае, до загрузки ленты. Существуют три места для установки этих свойств:

- В Visual Studio **свойства** окна.

- В конструкторе класса **ленты** класса.

- В `CreateRibbonExtensibilityObject` метод `ThisAddin`, `ThisWorkbook`, или `ThisDocument` класс проекта.

  Динамические меню предоставляют некоторые исключения. Можно создать новые элементы управления, задавать их свойства и затем добавить их в динамическое меню во время выполнения, даже после загрузки ленты, содержащей меню.

  Свойства элементов управления, добавляемые в динамическом меню и могут задаваться в любое время.

  Дополнительные сведения см. в разделе [свойства, которые становятся доступными только для чтения](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Задайте свойства в конструкторе ленты
 Можно задать свойства `Ribbon` элемента управления в конструкторе класса **ленты** класса. Должен появиться этот код после вызова `InitializeComponent` метод. В следующем примере добавляется новая кнопка в группу, если текущее время — 17:00 по тихоокеанскому времени (UTC-8) или более поздней версии.

 Добавьте следующий код.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 В визуальном элементе C# проектах, обновленных с Visual Studio 2008, конструктор отображается в файле кода ленты.

 В проектах Visual Basic или Visual C# проектов, созданных в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], конструктор отображается в файле кода конструктора лент. Этот файл называется *YourRibbonItem*. Designer.cs или *YourRibbonItem*. Designer.vb. Чтобы просмотреть этот файл в проектах Visual Basic, необходимо сначала щелкнуть **Показать все файлы** кнопка в обозревателе решений.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Задайте свойства в методе CreateRibbonExtensibilityObject
 Можно задать свойства `Ribbon` управления при переопределении `CreateRibbonExtensibilityObject` метод в `ThisAddin`, `ThisWorkbook`, или `ThisDocument` класс проекта. Дополнительные сведения о `CreateRibbonExtensibilityObject` метод, см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

 Следующий пример задает свойства ленты в `CreateRibbonExtensibilityObject` метод `ThisWorkbook` класс проекта книги Excel.

 Добавьте следующий код.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="ReadOnlyProperties"></a> Свойства, которые становятся доступными только для чтения
 Ниже приведены свойства, которые могут устанавливаться только до загрузки ленты.

> [!NOTE]
> Можно задать свойства элементов управления динамического меню в любое время. Эта таблица применяется в этом случае.

|Свойство|Класс элемента управления ленты|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Число столбцов**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**динамические**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Группы**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**положение**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Количество строк**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Вкладки**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Заголовок**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Задание свойств для лент, появляющихся в инспекторов Outlook
 Новый экземпляр ленты создается каждый раз при открытии инспектор, в котором отображается ленты. Тем не менее можно задать свойства, перечисленные в приведенной выше таблице только перед созданием первого экземпляра ленты. После первого, создается экземпляр эти свойства становятся доступными только для чтения, так как первый экземпляр определяет XML-файл используется для загрузки ленты в Outlook.

 Если у вас есть условную логику, которая задает любого из этих свойств отличается от значения, при создании других экземпляров ленты, этот код не будет действовать.

> [!NOTE]
> Убедитесь, что **имя** имеет значение для каждого элемента управления, добавляемые на ленту Outlook. Если добавить элемент управления на ленту Outlook во время выполнения, необходимо задать это свойство в коде. Если добавить элемент управления на ленту Outlook во время разработки, свойство Name задается автоматически.

## <a name="ribbon-control-events"></a>События элементов управления ленты
 Каждый класс элемента управления содержит одно или несколько событий. В следующей таблице описаны эти события.

|событие|Описание|
|-----------|-----------------|
|Нажмите кнопку|Происходит при щелчке элемента управления.|
|TextChanged|Происходит при изменении текста, поле или поле со списком.|
|ItemsLoading|Происходит при запросе коллекции элементов управления в офисе. Office кэширует в коллекцию элементов, пока код изменяет свойства элемента управления или вызове <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> метод.|
|ButtonClick|Происходит, когда кнопки в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> или <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> нажатии.|
|SelectionChanged|Происходит, когда выделение в <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> изменения.|
|DialogLauncherClick|Происходит при щелчке значку вызова диалогового окна в правом нижнем углу группы.|

 Обработчики событий для этих событий имеют следующие два параметра.

|Параметр|Описание|
|---------------|-----------------|
|*Отправитель*|<xref:System.Object> , Представляющий элемент управления, который вызвал событие.|
|*e*|Объект <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> , содержащий <xref:Microsoft.Office.Core.IRibbonControl>. Используйте этот элемент управления для доступа к любому свойству, которая недоступна в объектную модель ленты, предоставляемые [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|

## <a name="see-also"></a>См. также
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Обзор ленты](../vsto/ribbon-overview.md)
- [Практическое руководство. Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство: Обновления элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)
- [Практическое руководство. Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Практическое руководство. Экспорт лент из конструктора лент в XML-ленты](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Практическое руководство. Показывать ошибки надстройки пользовательского интерфейса](../vsto/how-to-show-add-in-user-interface-errors.md)
