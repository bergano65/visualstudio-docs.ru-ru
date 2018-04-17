---
title: Общие сведения об объектной модели ленты | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c0d6defc160d08d0c92dd21370144c1ef748e7e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ribbon-object-model-overview"></a>Общие сведения об объектной модели ленты
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Предоставляет строго типизированную объектную модель, можно использовать для получения и задания свойств элементов управления ленты во время выполнения. Например можно динамически заполнения элементов управления меню, или отображение и скрытие элементов управления в зависимости от контекста. Можно также добавить вкладок, групп и элементов управления на ленту, но только до загрузки ленты в приложение Office. Сведения см. в разделе [параметр свойства, становятся только для чтения](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Эта объектная модель ленты заключается главным образом [класса ленты](#RibbonClass), [события ленты](#RibbonEvents), и [классы элементов управления ленты](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Класс ленты  
 При добавлении нового **Лента (визуальный конструктор)** элемента в проект Visual Studio добавляет **ленты** класса в проект. **Ленты** класс наследует от <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> класса.  
  
 Этот класс отображается как разделяемый класс, распределенный между файл кода ленты и файл кода конструктора лент.  
  
##  <a name="RibbonEvents"></a> События ленты  
 **Ленты** класс содержит три следующих событий:  
  
|событие|Описание|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Вызывается, когда приложение Office загружает настройки ленты. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Обработчик событий автоматически добавляется в файл кода ленты. Этот обработчик событий можно используйте для выполнения пользовательского кода при загрузке ленты.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Позволяет кэшировать изображения в настройке ленты при ее загрузке. Если написать код для кэширования изображений ленты в этом обработчике событий можно получить некоторого улучшения производительности. Дополнительные сведения см. в разделе <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Возникает при закрытии экземпляра ленты.|  
  
##  <a name="RibbonControlClasses"></a> Элементы управления ленты  
 <xref:Microsoft.Office.Tools.Ribbon> Пространство имен содержит типы для каждого элемента управления, которое будет отображаться в **элементы управления ленты Office** группы **элементов**.  
  
 В следующей таблице показаны типа для каждого `Ribbon` элемента управления. Описание каждого элемента управления, см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
|Имя элемента управления|Имя класса|  
|------------------|----------------|  
|**Поле**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Раскрывающийся список**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Поля ввода**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Коллекция**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Группа**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Вкладка**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**Элемент управления ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> Пространства имен используется префикс «Лента» для этих типов, чтобы избежать конфликт имен с именами классов элементов управления в <xref:System.Windows.Forms> пространства имен.  
  
 При добавлении элемента управления в конструктор ленты конструктор лент объявляет класс для этого элемента управления как поле в файле кода конструктора лент.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Типовые задачи с помощью свойств элементов управления ленты  
 Каждый `Ribbon` элемент управления содержит свойства, которые можно использовать для выполнения различных задач, таких как назначение метку для элемента управления или скрытие и отображение элементов управления.  
  
 В некоторых случаях свойства становятся доступными только для чтения после загрузки ленты или после добавления элемента управления в динамическом меню. Дополнительные сведения см. в разделе [Установка свойств этого Become только для чтения](#SettingReadOnlyProperties).  
  
 В следующей таблице описаны некоторые задачи, которые можно выполнять с помощью `Ribbon` свойств элемента управления.  
  
|Для выполнения этой задачи|Выполните следующее.|  
|--------------------|--------------|  
|Скрытие или отображение элемента управления.|Используйте свойство Visible.|  
|Включение и отключение элемента управления.|Свойство Enabled.|  
|Установите размер элемента управления.|Свойство ControlSize.|  
|Получите изображение, отображаемое на элементе управления.|Свойство изображения.|  
|Изменение метки элемента управления.|Свойство метки.|  
|Добавление пользовательских данных в элемент управления.|Используйте свойство Tag.|  
|Получить элементы в <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, или<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> элемент управления.|Используйте свойство Items.|  
|Добавление элементов к <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> элемента управления.|Используйте свойство Items.|  
|Добавление элементов управления <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Используйте свойство Items.<br /><br /> Добавить элементы управления для <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> после загрузки ленты в приложение Office, необходимо задать <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> свойства **true** до загрузки ленты в приложение Office. Сведения см. в разделе [параметр свойства, становятся только для чтения](#SettingReadOnlyProperties).|  
|Получение выбранного элемента <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Свойство SelectedItem. Для <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, используйте <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> свойство.|  
|Получение групп <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Используйте свойство <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Укажите число строк и столбцов в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Используйте <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> и <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> свойства.|  
  
##  <a name="SettingReadOnlyProperties"></a> Настройка свойств, которые становятся доступными только для чтения  
 Некоторые свойства можно задать только до загрузки ленты. Существует три места для установки этих свойств:  
  
-   В Visual Studio **свойства** окна.  
  
-   В конструкторе **ленты** класса.  
  
-   В методе CreateRibbonExtensibilityObject `ThisAddin`, `ThisWorkbook`, или `ThisDocument` класс проекта.  
  
 Динамические меню предоставляют некоторые исключения. Можно создавать новые элементы управления, задавать их свойства и добавить их в динамическое меню во время выполнения, даже после загрузки ленты, содержащей меню.  
  
 В любое время можно установить свойства элементов управления, добавляемые в динамическом меню.  
  
 Дополнительные сведения см. в разделе [, Become только для чтения свойства](#ReadOnlyProperties).  
  
### <a name="setting-properties-in-the-constructor-of-the-ribbon"></a>Установка свойств в конструкторе ленты  
 Можно задать свойства `Ribbon` управления в конструкторе **ленты** класса. Этот код должен находиться после вызова метода `InitializeComponent` метод. В следующем примере добавляется новая кнопка в группу, если текущее время — 17:00 по тихоокеанскому времени (UTC-8) или более поздней версии.  
  
 Добавьте следующий код.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 В проектах Visual C#, обновленных с Visual Studio 2008 конструктор отображается в файле кода ленты.  
  
 В проектах Visual Basic или в проектах Visual C#, созданных в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], конструктор отображается в файле кода конструктора лент. Этот файл называется *YourRibbonItem*. Designer.cs или *YourRibbonItem*. Designer.vb. Чтобы просмотреть этот файл в проектах Visual Basic, необходимо сначала щелкнуть **Показать все файлы** кнопку в обозревателе решений.  
  
### <a name="setting-properties-in-the-createribbonextensibilityobject-method"></a>Задание свойств в методе CreateRibbonExtensibilityObject  
 Можно задать свойства `Ribbon` управления при переопределении метода CreateRibbonExtensibilityObject в `ThisAddin`, `ThisWorkbook`, или `ThisDocument` класс проекта. Дополнительные сведения о методе CreateRibbonExtensibilityObject см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
 Следующий пример задает свойства ленты в методе CreateRibbonExtensibilityObject `ThisWorkbook` класс проекта книги Excel.  
  
 Добавьте следующий код.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Свойства, которые становятся доступными только для чтения  
 В следующей таблице показаны свойства, которые могут быть установлены только до загрузки ленты.  
  
> [!NOTE]  
>  В любое время можно установить свойства элементов управления динамического меню. Эта таблица не применяется в этом случае.  
  
|Свойство.|Класс элемента управления ленты|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Число столбцов**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**controlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**динамические**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Группы**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**Для ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**maxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Положение**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Количество строк**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Вкладки**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Заголовок**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="setting-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Задание свойств для лент, появляющихся в инспекторов Outlook  
 Новый экземпляр ленты создается каждый раз, когда пользователь открывает инспектор, в котором отображается ленты. Тем не менее можно задать свойства, перечисленные в приведенной выше таблице только перед созданием первого экземпляра ленты. После первого, создается экземпляр эти свойства доступны только для чтения, поскольку первый экземпляр определяет XML-файл используется для загрузки ленты в Outlook.  
  
 Если у вас есть условную логику, определяющую любого из этих свойств другое значение при создании других экземпляров ленты, этот код не будет действовать.  
  
> [!NOTE]  
>  Убедитесь, что **имя** свойство имеет значение для каждого элемента управления, добавляемого в ленту Outlook. Если добавить элемент управления на ленту Outlook во время выполнения, необходимо задать это свойство в коде. При добавлении элемента управления на ленту Outlook во время разработки свойство Name устанавливается автоматически.  
  
## <a name="ribbon-control-events"></a>События элементов управления ленты  
 Каждый класс элемента управления содержит одно или несколько событий. В следующей таблице описаны эти события.  
  
|событие|Описание|  
|-----------|-----------------|  
|Нажмите кнопку|Происходит при щелчке элемента управления.|  
|TextChanged|Происходит при изменении текста в текстовом поле или поле со списком.|  
|ItemsLoading|Происходит при запросе коллекции элементов управления с Office. Office кэширует коллекцию элементов, пока код не изменит свойства элемента управления или вызове <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> метода.|  
|ButtonClick|Происходит, когда кнопка в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> или <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> нажата.|  
|SelectionChanged|Возникает, когда выделение в <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> изменения.|  
|DialogLauncherClick|Происходит при щелчке значка запуска диалогового окна в правом нижнем углу группы.|  
  
 Обработчики событий для этих событий имеют следующие два параметра.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*Отправитель*|<xref:System.Object> Представляет элемент управления, вызвавший событие.|  
|*e*|Объект <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> , содержащий <xref:Microsoft.Office.Core.IRibbonControl>. Используйте этот элемент управления для доступа к любому свойству, недоступные в объектной модели ленты, предоставляемые [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Как: работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство: Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Как: Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)   
 [Как: Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Как: экспорт ленты из конструктора лент в XML-ленты](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Практическое руководство. Просмотр ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  