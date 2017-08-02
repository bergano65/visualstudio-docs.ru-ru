---
title: "Пошаговое руководство. Отображение в Outlook настраиваемых областей задач с сообщениями электронной почты"
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
  - "Outlook [разработка решений Office в Visual Studio], настраиваемые области задач"
  - "области задач [разработка решений Office в Visual Studio], отображение с сообщениями электронной почты"
  - "отображение - настраиваемые области задач (электронная почта)"
  - "электронная почта [разработка решений Office в Visual Studio], настраиваемые области задач"
  - "настраиваемые области задач [разработка решений Office в Visual Studio], отображение с сообщениями электронной почты"
ms.assetid: 04943967-a7ef-4876-9584-84ada427e3f3
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# Пошаговое руководство. Отображение в Outlook настраиваемых областей задач с сообщениями электронной почты
  В этом пошаговом руководстве показано, как отобразить уникальный экземпляр настраиваемой области задач для каждого созданного или открытого сообщения электронной почты. Пользователи могут отображать или скрывать настраиваемую область задач с помощью кнопки на ленте каждого сообщения электронной почты.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Чтобы отображать настраиваемую область задач с несколькими окнами проводника или инспектора, необходимо создать новый экземпляр настраиваемой области задач для каждого открытого окна. Дополнительные сведения о поведении настраиваемых областей задач в окнах Outlook см. в разделе [Настраиваемые области задач](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  В этом пошаговом руководстве код надстройки VSTO представлен небольшими частями для облегчения обсуждения логики кода.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Конструирование пользовательского интерфейса настраиваемой области задач.  
  
-   Создание пользовательского интерфейса настраиваемой ленты.  
  
-   Отображение пользовательского интерфейса настраиваемой ленты с сообщениями электронной почты.  
  
-   Создание класса для управления окнами инспектора и настраиваемыми областями задач.  
  
-   Инициализация и освобождение ресурсов, используемых надстройкой VSTO.  
  
-   Синхронизация выключателя на ленте с настраиваемой областью задач.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] или Microsoft Outlook 2010.  
  
 ![ссылка на видео](~/docs/data-tools/media/playvideo.gif "ссылка на видео") Связанные демонстрационные видеоролики см. на странице [Как использовать области задач в Outlook?](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## Создание проекта  
 Настраиваемые области задач реализуются в надстройках VSTO. Начните с создания проекта надстройки VSTO для Outlook.  
  
#### Создание нового проекта  
  
1.  Создайте проект **надстройки Outlook** с именем **OutlookMailItemTaskPane**. Используйте шаблон проекта **Надстройка Outlook**. Для получения дополнительной информации см. [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn.cs** или **ThisAddIn.vb** и добавляет проект **OutlookMailItemTaskPane** в **обозреватель решений**.  
  
## Проектирование пользовательского интерфейса настраиваемой области задач  
 Визуальный конструктор для настраиваемых областей задач не предусмотрен, но можно создать пользовательский элемент управления с нужным пользовательским интерфейсом. Настраиваемая область задач в этой надстройке VSTO имеет простой пользовательский интерфейс, содержащий элемент управления <xref:System.Windows.Forms.TextBox>. Далее в этом пошаговом руководстве вы добавите этот пользовательский элемент управления в настраиваемую область задач.  
  
#### Проектирование пользовательского интерфейса настраиваемой области задач  
  
1.  В **обозревателе решений**, щелкните проект **OutlookMailItemTaskPane**.  
  
2.  В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.  
  
3.  В диалоговом окне **Добавление нового элемента** измените имя нового пользовательского элемента управления на **TaskPaneControl**, а затем нажмите кнопку **Добавить**.  
  
     Пользовательский элемент управления откроется в конструкторе.  
  
4.  Перетащите элемент управления **TextBox** со вкладки **Стандартные элементы управления** на **панели элементов** в пользовательский элемент управления.  
  
## Конструирование пользовательского интерфейса ленты  
 Одна из целей этой надстройки VSTO заключается в том, чтобы предоставить пользователям возможность скрывать или отображать настраиваемую область задач с ленты каждого сообщения электронной почты. Чтобы обеспечить пользовательский интерфейс, создайте пользовательский интерфейс настраиваемой ленты, отображающий выключатель, который пользователь может щелкнуть, чтобы отобразить или скрыть настраиваемую область задач.  
  
#### Создание пользовательского интерфейса настраиваемой ленты  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите элемент **Лента \(визуальный конструктор\)**.  
  
3.  Измените имя новой ленты на **ManageTaskPaneRibbon** и нажмите кнопку **Добавить**.  
  
     В конструкторе ленты откроется файл **ManageTaskPaneRibbon.cs** или **ManageTaskPaneRibbon.vb** и отобразятся вкладка и группа, используемые по умолчанию.  
  
4.  В конструкторе ленты щелкните группу **group1**.  
  
5.  В окне **Свойства** задайте для свойства **Label** значение **Диспетчер области задач**.  
  
6.  Перетащите элемент управления ToggleButton со вкладки **Элементы управления ленты Office** на **панели элементов** в группу **Диспетчер области задач**.  
  
7.  Нажмите **toggleButton1**.  
  
8.  В окне **Свойства** задайте в свойстве **Label** значение **Показать область задач**.  
  
## Отображение пользовательского интерфейса настраиваемой ленты с сообщениями электронной почты  
 Настраиваемая область задач, которую вы создаете в этом пошаговом руководстве, должна появляться только с окнами инспектора, содержащими сообщения электронной почты. Поэтому задайте свойства таким образом, чтобы ваш пользовательский интерфейс настраиваемой ленты отображался только с этими окнами.  
  
#### Отображение пользовательского интерфейса настраиваемой ленты с сообщениями электронной почты  
  
1.  В конструкторе лент щелкните ленту **ManageTaskPaneRibbon**.  
  
2.  В окне **Свойства** щелкните раскрывающийся список рядом со свойством **RibbonType**, и выберите **Microsoft.Outlook.Mail.Compose** и **Microsoft.Outlook.Mail.Read**.  
  
## Создание класса для управления окнами инспектора и настраиваемыми областями задач  
 Существует несколько случаев, в которых надстройка VSTO должна определять, какая настраиваемая область задач связана с конкретным сообщением электронной почты. Это следующие случаи.  
  
-   Когда пользователь закрывает сообщение электронной почты. В этом случае надстройка VSTO должна удалить соответствующую настраиваемую область задач, чтобы ресурсы, используемые этой надстройкой VSTO, были правильно освобождены.  
  
-   Когда пользователь закрывает настраиваемую область задач. В этом случае надстройка VSTO должна обновить состояние выключателя на ленте сообщения электронной почты.  
  
-   Когда пользователь щелкает выключатель на ленте. В этом случае надстройка VSTO должна скрыть или отобразить соответствующую область задач.  
  
 Чтобы надстройка VSTO отслеживала, какая настраиваемая область задач связана с каждым открытым сообщением электронной почты, создайте пользовательский класс, который создает оболочку для пар объектов <xref:Microsoft.Office.Interop.Outlook.Inspector> и <xref:Microsoft.Office.Tools.CustomTaskPane>. Этот класс создает новый объект настраиваемой области задач для каждого сообщения электронной почты и удаляет настраиваемую область задач при закрытии соответствующего сообщения электронной почты.  
  
#### Создание класса для управления окнами инспектора и настраиваемыми областями задач  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши файл **ThisAddIn.cs** или **ThisAddIn.vb** и выберите в контекстном меню команду **Просмотреть код**.  
  
2.  Добавьте следующие инструкции в начало файла.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#2)]  
  
3.  Добавьте следующий код в файл **ThisAddIn.cs** или **ThisAddIn.vb** за пределами класса `ThisAddIn` \(для Visual C\# добавьте этот код в пространство имен `OutlookMailItemTaskPane`\). Класс `InspectorWrapper` управляет парой объектов <xref:Microsoft.Office.Interop.Outlook.Inspector> и <xref:Microsoft.Office.Tools.CustomTaskPane>. Вы завершите определение этого класса в следующих шагах.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#3)]  
  
4.  Добавьте следующий конструктор после кода, добавленного на предыдущем шаге. Этот конструктор создает и инициализирует новую настраиваемую область задач, связанную с переданным объектом <xref:Microsoft.Office.Interop.Outlook.Inspector>. В C\# этот конструктор также присоединяет обработчики событий к событию <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> объекта <xref:Microsoft.Office.Interop.Outlook.Inspector> и к событию <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> объекта <xref:Microsoft.Office.Tools.CustomTaskPane>.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#4)]  
  
5.  Добавьте следующий метод после кода, добавленного на предыдущем шаге. Этот метод является обработчиком событий для события <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> объекта <xref:Microsoft.Office.Tools.CustomTaskPane>, содержащегося в классе `InspectorWrapper`. Этот код обновляет состояние выключателя всякий раз, когда пользователь открывает или закрывает настраиваемую область задач.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#5)]  
  
6.  Добавьте следующий метод после кода, добавленного на предыдущем шаге. Этот метод является обработчиком событий для события <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> объекта <xref:Microsoft.Office.Interop.Outlook.Inspector>, содержащего текущее сообщение электронной почты. Этот обработчик событий освобождает ресурсы при закрытии сообщения электронной почты. Он также удаляет текущую область задач из коллекции `CustomTaskPanes`. Это помогает предотвратить появление нескольких экземпляров настраиваемой области задач при открытии следующего сообщения электронной почты.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#6)]  
  
7.  Добавьте следующий код после кода, добавленного на предыдущем шаге. Далее в этом пошаговом руководстве вы будете вызывать это свойство из метода в пользовательском интерфейсе настраиваемой ленты, чтобы отобразить или скрыть настраиваемую область задач.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#7)]  
  
## Инициализация и освобождение ресурсов, используемых надстройкой  
 Добавьте код в класс `ThisAddIn` для инициализации надстройки VSTO при ее загрузке, а также для освобождения ресурсов, используемых этой надстройкой VSTO, при ее выгрузке. Вы инициализируете надстройку VSTO, настроив обработчик событий для события <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> и передав все существующие сообщения электронной почты в этот обработчик событий. Когда надстройка VSTO выгружается, отсоедините этот обработчик событий и освободите объекты, используемые надстройкой VSTO.  
  
#### Инициализация и освобождение ресурсов, используемых надстройкой VSTO  
  
1.  В файле **ThisAddIn.cs** или **ThisAddIn.vb** найдите определение класса `ThisAddIn`.  
  
2.  Добавьте в класс `ThisAddIn` следующие объявления.  
  
    -   Поле `inspectorWrappersValue` содержит все объекты <xref:Microsoft.Office.Interop.Outlook.Inspector> и `InspectorWrapper`, которыми управляет надстройка VSTO.  
  
    -   Поле `inspectors` содержит ссылку на коллекцию окон инспектора в текущем экземпляре Outlook. Эта ссылка не позволит сборщику мусора освободить память, содержащую обработчик событий для события <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>, который вы объявите на следующем шаге.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#8)]  
  
3.  Замените метод `ThisAddIn_Startup` следующим кодом. Этот код присоединяет обработчик событий к событию <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> и передает каждый существующий объект <xref:Microsoft.Office.Interop.Outlook.Inspector> в данный обработчик событий. Если пользователь загружает надстройку VSTO, когда Outlook уже запущен, надстройка VSTO использует эти сведения для создания настраиваемых областей задач для всех уже открытых сообщений электронной почты.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_OutlookMailItemTaskPane#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#9)]  
  
4.  Замените метод `ThisAddIn_ShutDown` следующим кодом. Этот код отсоединяет обработчик событий <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> и освобождает объекты, используемые надстройкой VSTO.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_OutlookMailItemTaskPane#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#10)]  
  
5.  Добавьте следующий обработчик событий <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> в класс `ThisAddIn`. Если новый <xref:Microsoft.Office.Interop.Outlook.Inspector> содержит сообщение электронной почты, данный метод создает экземпляр нового объекта `InspectorWrapper` для управления связью между сообщением электронной почты и соответствующей областью задач.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_OutlookMailItemTaskPane#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#11)]  
  
6.  Добавьте в класс `ThisAddIn` указанное ниже свойство. Это свойство предоставляет закрытое поле `inspectorWrappersValue` коду за пределами класса `ThisAddIn`.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_OutlookMailItemTaskPane#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#12)]  
  
## Контрольная точка  
 Постройте проект, чтобы убедиться, что компиляция выполняется без ошибок.  
  
#### Построение проекта  
  
1.  В **обозревателе решений** щелкните проект **OutlookMailItemTaskPane** правой кнопкой мыши и выберите пункт **Сборка**. Убедитесь, что проект компилируется без ошибок.  
  
## Синхронизация выключателя на ленте с настраиваемой областью задач  
 Выключатель будет выглядеть как нажатый, когда область задач отображена, и как не нажатый, когда область задач скрыта. Чтобы синхронизировать состояние этой кнопки с настраиваемой областью задач, измените обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> этого выключателя.  
  
#### Синхронизация настраиваемой области задач с выключателем  
  
1.  В конструкторе ленты дважды щелкните выключатель **Показать область задач**.  
  
     Visual Studio автоматически создает обработчик событий с именем `toggleButton1_Click`, который обрабатывает событие <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> выключателя. Visual Studio также открывает файл **ManageTaskPaneRibbon.cs** или **ManageTaskPaneRibbon.vb** в редакторе кода.  
  
2.  Добавьте следующие инструкции в начале файла **ManageTaskPaneRibbon.cs** или **ManageTaskPaneRibbon.vb**.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ManageTaskPaneRibbon.vb#14)]  
  
3.  Замените обработчик событий `toggleButton1_Click` следующим кодом. Когда пользователь нажимает выключатель, этот метод отображает или скрывает настраиваемую область задач, связанную с текущим окном инспектора.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ManageTaskPaneRibbon.vb#15)]  
  
## Тестирование проекта  
 Когда вы запускаете отладку проекта, открывается Outlook и загружается надстройка VSTO. Надстройка VSTO отображает уникальный экземпляр настраиваемой области задач для каждого открываемого сообщения электронной почты. Создайте несколько новых сообщений электронной почты для проверки кода.  
  
#### Тестирование надстройки VSTO  
  
1.  Нажмите клавишу F5.  
  
2.  В Outlook нажмите кнопку **Создать**, чтобы создать новое сообщение электронной почты.  
  
3.  На ленте сообщения электронной почты щелкните вкладку **Надстройки**, а затем нажмите кнопку **Показать область задач**.  
  
     Убедитесь, что вместе с сообщением электронной почты отображается область задач с заголовком **Моя область задач**.  
  
4.  В этой области задач введите в текстовом поле **Первая область задач**.  
  
5.  Закройте область задач.  
  
     Убедитесь, что состояние кнопки **Показать область задач** изменилось, и она больше не выглядит нажатой.  
  
6.  Снова нажмите кнопку **Показать область задач**.  
  
     Убедитесь, что область задач открывается и текстовое поле по\-прежнему содержит строку **Первая область задач**.  
  
7.  В Outlook нажмите кнопку **Создать**, чтобы создать второе сообщение электронной почты.  
  
8.  На ленте сообщения электронной почты щелкните вкладку **Надстройки**, а затем нажмите кнопку **Показать область задач**.  
  
     Убедитесь, что вместе с сообщением электронной почты отображается область задач с заголовком **Моя область задач**, и текстовое поле в этой области задач пустое.  
  
9. В этой области задач введите в текстовом поле **Вторая область задач**.  
  
10. Перейдите в первое сообщение электронной почты.  
  
     Убедитесь, что область задач, связанная с этим сообщением электронной почты, по\-прежнему отображает **Первая область задач** в текстовом поле.  
  
 Эта надстройка VSTO также обрабатывает более сложные сценарии, которые вы можете попробовать. Например, можно проверить поведение при просмотре сообщений электронной почты с помощью кнопок **Следующее сообщение** и **Предыдущее сообщение**. Можно также проверить поведение, выгрузив надстройку VSTO, открыв несколько сообщений электронной почты и снова загрузив надстройку VSTO.  
  
## Следующие действия  
 Дополнительные сведения о создании настраиваемых областей задач см. в следующих разделах.  
  
-   Создание настраиваемой области задач в надстройке VSTO для другого приложения. Дополнительные сведения о приложениях, поддерживающих настраиваемые области задач, см. в разделе [Настраиваемые области задач](../vsto/custom-task-panes.md).  
  
-   Автоматизация приложения Microsoft Office с помощью настраиваемой области задач. Для получения дополнительной информации см. [Руководство. Автоматизация приложения в настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Создание в Excel кнопки ленты, которая может использоваться для скрытия или отображения настраиваемой области задач. Дополнительные сведения см. в разделе [Пошаговое руководство. Синхронизация настраиваемой области задач с кнопкой на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## См. также  
 [Настраиваемые области задач](../vsto/custom-task-panes.md)   
 [Практическое руководство. Добавление настраиваемой панели задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Руководство. Автоматизация приложения в настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Пошаговое руководство. Синхронизация настраиваемой области задач с кнопкой на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)   
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  