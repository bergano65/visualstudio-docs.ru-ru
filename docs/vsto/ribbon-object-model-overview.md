---
title: "Общие сведения об объектной модели ленты | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "лента [разработка решений Office в Visual Studio], объектная модель"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Общие сведения об объектной модели ленты
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] предоставляет строго типизированную объектную модель, которую можно использовать для получения и установки свойств элементов управления ленты во время выполнения.  Например, можно динамически наполнять элементы управления меню, а также скрывать или показывать элементы управления в зависимости от контекста.  Можно также добавить вкладки, группы и элементов управления на ленте, но только до лентой загружает приложением office.  Дополнительные сведения см. в разделе [Установка свойств, становящихся свойствами только для чтения](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Данная объектная модель ленты в основном состоит из [класса ленты](#RibbonClass), [событий ленты](#RibbonEvents) и [классов элементов управления ленты](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Класс ленты  
 При добавлении нового элемента **Визуальный конструктор ленты \(\)** в проект в Visual Studio добавляет в проект класс **Ribbon**.  Класс **Ribbon** является производным классом класса <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>.  
  
 Этот класс отображается как разделяемый класс, который делится между файлом кода ленты и файлом кода конструктора лент.  
  
##  <a name="RibbonEvents"></a> События ленты  
 Класс **Ribbon** содержит следующие события: 3  
  
|Событие|Описание|  
|-------------|--------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Возникает при загрузке настройки ленты приложением office.  Автоматически добавляется обработчик событий <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> в файле кода ленты.  Этот обработчик событий для выполнения пользовательского кода при загрузке ленты.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Позволяет кэшировать изображения в настройке ленты при загрузке ленты.  Можно получить небольшой прибавку производительности при написании кода для кэширования кода ленты в этом обработчике событий.  Для получения дополнительной информации см. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Вызывается, когда экземпляр ленты закрывает.|  
  
##  <a name="RibbonControlClasses"></a> Элементы управления ленты  
 Пространство имен <xref:Microsoft.Office.Tools.Ribbon> содержит типы для каждого элемента управления, отображаемого в группе **Элементы управления ленты Office** в панели **Панель элементов**.  
  
 В следующей таблице показан тип для каждого элемента управления `Ribbon`.  Описание каждого элемента управления см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
|Имя элемента управления|Имя класса|  
|-----------------------------|----------------|  
|**Поле**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Кнопка**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Коллекция**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Группа**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Метка**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Меню**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Разделитель**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Вкладка**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 Пространство имен <xref:Microsoft.Office.Tools.Ribbon> использует префикс "Ribbon" для этих типов, чтобы избежать совпадения с именами классов элементов управления в пространстве имен <xref:System.Windows.Forms>.  
  
 При добавлении элемента управления в конструктор ленты конструктор объявляет класс для этого элемента управления как поле в файле кода конструктора ленты.  
  
### Типичные задачи использования свойств элементов управления ленты  
 Каждый элемент управления `Ribbon` содержит свойства, которые можно использовать для выполнения различных задач, например присвоить метку к элементу управления или скрывать и отображать элементы управления.  
  
 В некоторых случаях свойства становятся свойствами только для чтения после загрузки ленты или после добавления элемента управления в динамическое меню.  Дополнительные сведения см. в разделе [Установка свойств, становящихся свойствами только для чтения](#SettingReadOnlyProperties).  
  
 В следующей таблице описаны некоторые задачи, которые можно выполнить с помощью свойств элемента управления `Ribbon`.  
  
|Для данной задачи:|Действия:|  
|------------------------|---------------|  
|Скрытие или отображение элемента управления.|Используйте свойство Visible.|  
|Включение и отключение элемента управления.|Используйте свойство Enabled.|  
|Установка размеров элемента управления.|Используйте свойство ControlSize.|  
|Получение изображения, отображаемого на элементе управления.|Используйте свойство Image.|  
|Изменение метки элемента управления.|Используйте свойство Label.|  
|Добавление пользовательских данных в элемент управления.|Используйте свойство Tag.|  
|Получение элементов в элементах управления <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> или<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.|Используйте свойство Items.|  
|Добавление элементов в элементы управления <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Используйте свойство Items.|  
|Добавление элементов управления в <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Используйте свойство Items.<br /><br /> Чтобы добавить элементы управления <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> после загрузки ленты в приложение office, необходимо присвоить свойству <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> значение **true** до загрузки ленты в приложение office.  Дополнительные сведения см. в разделе [Установка свойств, становящихся свойствами только для чтения](#SettingReadOnlyProperties).|  
|Получение выбранного элемента <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Используйте свойство SelectedItem.  Для элемента управления <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> следует использовать свойство <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>.|  
|Получение групп в <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Используйте свойство <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Указание числа строк и столбцов, отображаемых в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Используйте свойства <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> и <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>.|  
  
##  <a name="SettingReadOnlyProperties"></a> Установка свойств, становящихся свойствами только для чтения  
 Некоторые свойства можно установить только до загрузки ленты.  Существует три места для установки этих свойств:  
  
-   в окне **Свойства** Visual Studio;  
  
-   В конструкторе класса **Ribbon**.  
  
-   В методе CreateRibbonExtensibilityObject класса `ThisAddin`, `ThisWorkbook` или `ThisDocument` проекта.  
  
 Динамические меню предоставляют некоторые исключения.  Можно создать новые элементы управления, задать соответствующих свойств, а затем добавлять в динамического меню во время выполнения, даже после загрузки ленты, содержащей меню.  
  
 Свойства элементов управления, добавляемых в динамического меню, можно задавать в любой момент времени.  
  
 Дополнительные сведения см. в разделе [Свойства, становящиеся свойствами только для чтения](#ReadOnlyProperties).  
  
### Задание свойств в конструкторе ленты  
 Можно задать свойства элемента управления `Ribbon` в конструктор класса **Ribbon**.  После вызова метода `InitializeComponent` должен появиться этот код.  Следующий пример добавляет в группу новую кнопку, если текущее время равно 17:00 по тихоокеанскому времени \(UTC\-8\) или позже.  
  
 Добавьте следующий код.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 В проектах Visual C\# — \#, обновленных с Visual Studio 2008, конструктор отображается в файле кода ленты.  
  
 В проектах Visual Basic, или в проектах Visual C\# — \#, созданных в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], конструктор отображается в файле кода конструктора лент.  Этот файл является *YourRibbonItem*. Designer.cs или *YourRibbonItem*. Designer.vb.  Чтобы отобразить этот файл в проектах Visual Basic, сначала необходимо нажать кнопку **Показать все файлы** в обозревателе решений.  
  
### Задание свойств в методе CreateRibbonExtensibilityObject  
 Можно задать свойства элемента управления `Ribbon` при переопределении метода CreateRibbonExtensibilityObject в `ThisAddin`, `ThisWorkbook` или в классе `ThisDocument` проекта.  Дополнительные сведения о методе CreateRibbonExtensibilityObject см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
 Следующий пример задает свойства ленты в методе CreateRibbonExtensibilityObject класса `ThisWorkbook` проекта рабочей книги Excel.  
  
 Добавьте следующий код.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> Свойства, становящиеся свойствами только для чтения  
 Следующая таблица показывает свойства, которые можно установить только до загрузки ленты:  
  
> [!NOTE]  
>  Свойства элементов управления динамического меню можно задавать в любой момент времени.  В этом случае сведения данной таблицы не актуальны.  
  
|Свойство|Класс элемента управления ленты|  
|--------------|-------------------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Динамический**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groups**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Имя**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Положение**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Табуляции**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Заголовок**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Установка свойств для лент, отображаемых в окнах инспекторов Outlook  
 Новый экземпляр ленты создается каждый раз при открытии пользователем в инспекторе, ленты.  Однако можно задать свойства, перечисленные в таблице выше только до создания первого экземпляра ленты.  После создания первого экземпляра эти свойства становятся свойствами только для чтения, поскольку первый экземпляр определяет файл XML, используемый outlook для загрузки ленты.  
  
 При наличии условной логики, которая задает любое из этих свойств в другой значение при создании других экземпляров ленты, этот код не будет иметь эффекта.  
  
> [!NOTE]  
>  Убедитесь, что свойство **Имя** установлено для каждого элемента управления, добавляемого в ленте outlook.  При добавлении элемента управления на ленте outlook во время выполнения, необходимо установить это свойство в коде.  При добавлении элемента управления на ленте outlook во время разработки свойство Name устанавливается автоматически.  
  
## События элементов управления ленты  
 Каждый класс элемента управления содержит одно или несколько событий.  В следующей таблице приведено описание этих событий:  
  
|Событие|Описание|  
|-------------|--------------|  
|Click|Происходит при щелчке на элементе управления.|  
|TextChanged|Происходит при изменении текста в текстовом поле или поле со списком.|  
|ItemsLoading|Происходит при запросе коллекции Items элемента управления приложением Office.  Office кэширует коллекцию Items до тех пор, пока код не изменит свойства элемента управления, или не будет вызван метод <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>.|  
|ButtonClick|Происходит при нажатии кнопки в <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> или <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>.|  
|SelectionChanged|Происходит при изменении выделения в <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> или <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|  
|DialogLauncherClick|Происходит при щелчке по значку вызова диалогового окна в правом нижнем углу группы.|  
  
 Обработчики событий для этих событий имеют два параметра:  
  
|Параметр|Описание|  
|--------------|--------------|  
|*sender*|Объект <xref:System.Object>, представляющий элемент управления, который вызвал событие.|  
|*e*|Объект <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>, содержащий свойство <xref:Microsoft.Office.Core.IRibbonControl>.  Используйте этот элемент управления для доступа к любому недоступному в объектной модели ленты свойству, предоставляемому средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## См. также  
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Практическое руководство. Работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)   
 [Практическое руководство. Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Практическое руководство. Экспорт лент из конструктора лент в XML-ленты](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Практическое руководство. Просмотр ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  