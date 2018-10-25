---
title: Привязка элементов управления WPF к набору данных | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19189e63a3fb3fdfa3016cb2643cc34a193a2a52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893004"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Привязка элементов управления WPF к набору данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В этом пошаговом руководстве вы создадите приложение WPF, содержащее элементы управления с привязкой к данным. Эти элементы управления привязаны к записям продуктов, инкапсулированным в набор данных. Вы также добавите кнопки для просмотра продуктов и сохранения изменений в записях продуктов.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
- Создание приложения WPF и набора данных, сформированного из данных в учебной базе данных AdventureWorksLT.  
  
- Создание набора элементов управления с привязкой к данным путем перетаскивания таблицы данных из **источников данных** окна в окно в конструкторе WPF.  
  
- Создание кнопок для перехода вперед и назад по записям продуктов.  
  
- Создание кнопки для сохранения изменений, вносимых пользователем в записи продуктов, в таблице данных и базовом источнике данных.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Доступ к запущенному экземпляру SQL Server или SQL Server Express с подключенной учебной базой данных AdventureWorksLT. Можно загрузить базу данных AdventureWorksLT с [веб-сайте CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Перед изучением приведенных ниже концепций будет полезно, хотя и не обязательно, ознакомиться со следующим пошаговым руководством.  
  
- Наборы данных и адаптеры таблицы. Дополнительные сведения см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) и [TableAdapter Overview](../data-tools/tableadapter-overview.md).  
  
- Работа с Конструктором WPF. Дополнительные сведения см. в разделе [WPF и Silverlight Обзор конструктора](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Привязка данных WPF. Более подробную информацию см. в разделе [Общие сведения о связывании данных](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Создание проекта  
 Создайте новый проект WPF. Этот проект будет отображать записи продуктов.  
  
#### <a name="to-create-the-project"></a>Создание проекта  
  
1.  Запустите Visual Studio.  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  Разверните **Visual Basic** или **Visual C#**, а затем выберите **Windows**.  
  
4.  Выберите **приложение WPF** шаблона проекта.  
  
5.  В **имя** введите `AdventureWorksProductsEditor` и нажмите кнопку **ОК**.  
  
     Visual Studio создает `AdventureWorksProductsEditor` проекта.  
  
## <a name="create-a-dataset-for-the-application"></a>Создание набора данных для приложения  
 Перед созданием элементов управления с привязкой к данным, необходимо определить модель данных для вашего приложения и добавьте его в **источников данных** окна. В данном пошаговом руководстве вы создадите набор данных для использования в качестве модели данных.  
  
#### <a name="to-create-a-dataset"></a>Создание набора данных  
  
1.  В меню **Данные** выберите команду **Показать источники данных**.  
  
     **Источников данных** откроется окно.  
  
2.  В окне **Источники данных** выберите **Добавить новый источник данных**.  
  
     **Конфигурации источника данных**откроется мастер.  
  
3.  На **Выбор типа источника данных** выберите **базы данных**, а затем нажмите кнопку **Далее**.  
  
4.  На **Выбор модели базы данных** выберите **набора данных**, а затем нажмите кнопку **Далее**.  
  
5.  На **Выбор подключения к данным** странице, выберите один из следующих вариантов:  
  
    -   Если подключение данных к базе данных AdventureWorksLT доступно в раскрывающемся списке, выберите его и нажмите кнопку **Далее**.  
  
    -   Нажмите кнопку **новое подключение**и создайте подключение к базе данных AdventureWorksLT.  
  
6.  На **сохранение подключения в файле конфигурации приложения** выберите **Да, сохранить подключение как** флажок и нажмите кнопку **Далее**.  
  
7.  На **Выбор объектов базы данных** странице, разверните узел **таблиц**, а затем выберите **продукт (SalesLT)** таблицы.  
  
8.  Нажмите кнопку **Готово**.  
  
     Visual Studio добавляет в проект новый файл AdventureWorksLTDataSet.xsd, и оно добавляет соответствующий **AdventureWorksLTDataSet** элемент **источников данных** окна. Файл AdventureWorksLTDataSet.xsd определяет типизированный набор данных с именем `AdventureWorksLTDataSet` и адаптер таблицы с именем `ProductTableAdapter`. Позднее в рамках данного пошагового руководства вы воспользуетесь `ProductTableAdapter` для заполнения набора данных данными и сохранения изменений в базу данных.  
  
9. Выполните построение проекта.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Изменение метода заполнения по умолчанию адаптера таблицы  
 Чтобы заполнить набор данных данными, используйте метод `Fill` объекта `ProductTableAdapter`. По умолчанию метод `Fill` заполняет `ProductDataTable` в `AdventureWorksLTDataSet` со всеми строками данных из таблицы продукта. Вы можете изменить этот метод, чтобы он возвращал только подмножество строк. В рамках данного руководства измените метод `Fill` для возврата только строк для продуктов с фотографиями.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Загрузка строк продуктов с фотографиями  
  
1.  В **обозревателе решений**, дважды щелкните файл AdventureWorksLTDataSet.xsd.  
  
     Открывается Конструктор наборов данных.  
  
2.  В конструкторе щелкните правой кнопкой мыши **Fill,GetData()** запроса и выберите **Настройка**.  
  
     **Настройки адаптера таблицы**откроется мастер.  
  
3.  В **введите инструкцию SQL** странице, добавьте следующее предложение WHERE после `SELECT` инструкции в текстовом поле.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Нажмите кнопку **Готово**.  
  
## <a name="define-the-user-interface"></a>Определение пользовательского интерфейса  
 Добавьте несколько кнопок в окно, изменив в XAML в Конструкторе WPF. Позднее в рамках данного пошагового руководства вы добавите код, позволяющий пользователям выполнять прокрутку и сохранять изменения записей продуктов с помощью этих кнопок.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Определение пользовательского интерфейса окна  
  
1.  В **обозревателе решений**, дважды щелкните файл MainWindow.xaml.  
  
     Открывается окно в Конструкторе WPF.  
  
2.  В представлении [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] конструктора добавьте следующий код между тегами `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Выполните построение проекта.  
  
## <a name="createdata-bound-controls"></a>Элементы управления с привязкой создания  
 Создание элементов управления, отображающие записи клиентов, перетащив `Product` таблицу **источников данных** окно в конструктор WPF.  
  
#### <a name="to-create-data-bound-controls"></a>Порядок создания элементов управления с привязкой к данным  
  
1.  В **источников данных** окно, щелкните стрелку раскрывающегося меню **продукта** узел и выберите **сведения**.  
  
2.  Разверните **продукта** узла.  
  
3.  В этом примере некоторые поля не будут отображаться, поэтому щелкните раскрывающееся меню рядом со следующих узлов и выберите **None**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Щелкните стрелку раскрывающегося меню рядом с **ThumbNailPhoto** узел и выберите **изображение**.  
  
    > [!NOTE]
    >  По умолчанию элементы в **источников данных** окна, представляющих изображения имеют элементы управления по умолчанию, равным **None**. Это вызвано тем, что изображения хранятся в базах данных в виде байтовых массивов, которые могут содержать все — от простого массива байтов до исполняемого файла или большого приложения.  
  
5.  Из **источников данных** окно, перетащите **продукта** узел на строку сетки под строкой с кнопками.  
  
     Visual Studio создает XAML, который определяет набор элементов управления, привязанных к данным в **продуктов** таблицы. Также создается код, который загружает эти данные. Дополнительные сведения о созданных XAML и кода, см. в разделе [элементы управления WPF, привязка к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  В конструкторе щелкните текстовое поле рядом с полем **идентификатор продукта** метки.  
  
7.  В **свойства** окно, выберите флажок рядом с полем **IsReadOnly** свойство.  
  
## <a name="navigating-product-records"></a>Навигация по записям продуктов  
 Добавьте код, позволяющий пользователям выполнять прокрутку записей продуктов с помощью **\<** и **>** кнопки.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Предоставление пользователям возможности навигации по записям продуктов  
  
1.  В конструкторе, дважды щелкните **<** кнопки на поверхности окна.  
  
     Visual Studio открывает файл кода и создает новую `backButton_Click` обработчик событий для <xref:System.Windows.Controls.Primitives.ButtonBase.Click> событий.  
  
2.  Изменить `Window_Loaded` обработчик событий, поэтому `ProductViewSource`, `AdventureWorksLTDataSet`, и `AdventureWorksLTDataSetProductTableAdapter` вне пределов метода, и доступны всей форме. Объявите только их глобальным в форму и назначьте их в `Window_Loaded` обработчик событий, аналогичную следующей:  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3.  Добавьте следующий код в обработчик событий `backButton_Click` .  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4.  Вернитесь в конструктор и дважды щелкните **>** кнопки.  
  
5.  Добавьте следующий код в обработчик событий `nextButton_Click` .  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>SaveChanges в записях продуктов  
 Добавьте код, позволяющий пользователям сохранять изменения в записях продуктов с помощью **сохранить изменения** кнопки.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Добавление возможности сохранения изменений в записях продуктов  
  
1.  В конструкторе, дважды щелкните **сохранить изменения** кнопки.  
  
     Visual Studio открывает файл кода и создает новую `saveButton_Click` обработчик событий для <xref:System.Windows.Controls.Primitives.ButtonBase.Click> событий.  
  
2.  Добавьте следующий код в обработчик событий `saveButton_Click` .  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    >  В этом примере для сохранения изменений используется метод `Save` объекта `TableAdapter`. В данном пошаговом руководстве это целесообразно, так как изменяется только одна таблица данных. Если необходимо сохранить изменения нескольких таблиц, можно воспользоваться методом `UpdateAll` объекта `TableAdapterManager`, который Visual Studio создает вместе с вашим набором данных. Дополнительные сведения см. в разделе [Общие сведения о компоненте TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Тестирование приложения  
 Выполните сборку и запуск приложения. Убедитесь, что вы можете просмотреть и обновить записи продуктов.  
  
#### <a name="to-test-the-application"></a>Тестирование приложения  
  
1.  Нажмите клавишу **F5**.  
  
     Выполняется сборка и запуск приложения. Проверьте следующее.  
  
    -   Текстовые поля отображают данные из первой записи продукта с фотографией. Этот продукт имеет идентификатор 713 и имя **Long-Sleeve Logo Jersey, S**.  
  
    -   Можно щелкнуть **>** или **<** для перехода по другим записям продуктов.  
  
2.  В одной из записей продуктов измените **размер** значение, а затем нажмите кнопку **сохранить изменения**.  
  
3.  Закройте приложение, а затем перезапустите приложение, нажав клавишу **F5** в Visual Studio.  
  
4.  Перейдите к измененной записи продукта и убедитесь, что изменения сохранены.  
  
5.  Закройте приложение.  
  
## <a name="next-steps"></a>Следующие шаги  
 После прохождения пошагового руководства вы можете выполнить следующие задачи.  
  
-   Сведения об использовании **источников данных** окно в Visual Studio для привязки WPF элементы управления в другие типы источников данных. Дополнительные сведения см. в разделе [элементы управления WPF, привязка к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Сведения об использовании **источников данных** окно в Visual Studio для отображения связанных данных (т. е. данные в родительско дочернее отношение) в элементах управления WPF. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение связанных данных в приложении WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF и общие сведения о конструкторе Silverlight](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Общие сведения о привязке данных](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

