---
title: Bind WPF controls to a dataset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f0ad4ea108cb0ec3b874c7f360be2e1f0e25ef45
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299423"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Привязка элементов управления WPF к набору данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы создадите приложение WPF, содержащее элементы управления с привязкой к данным. Эти элементы управления привязаны к записям продуктов, инкапсулированным в набор данных. Вы также добавите кнопки для просмотра продуктов и сохранения изменений в записях продуктов.

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание приложения WPF и набора данных, сформированного из данных в учебной базе данных AdventureWorksLT.

- Создание набора привязанных к данным элементов управления посредством перетаскивания таблицы данных из окна **Источники данных** в окно в конструкторе WPF.

- Создание кнопок для перехода вперед и назад по записям продуктов.

- Создание кнопки для сохранения изменений, вносимых пользователем в записи продуктов, в таблице данных и базовом источнике данных.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Необходимые компоненты
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Доступ к запущенному экземпляру SQL Server или SQL Server Express с подключенной учебной базой данных AdventureWorksLT. You can download the AdventureWorksLT database from the [CodePlex Web site](https://go.microsoft.com/fwlink/?linkid=87843).

  Перед изучением приведенных ниже концепций будет полезно, хотя и не обязательно, ознакомиться со следующим пошаговым руководством.

- Наборы данных и адаптеры таблицы. For more information, see [Dataset tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Работа с Конструктором WPF. For more information, see [WPF and Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Привязка данных WPF. Более подробную информацию см. в разделе [Общие сведения о связывании данных](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-project"></a>Создание проекта
 Создайте новый проект WPF. Этот проект будет отображать записи продуктов.

#### <a name="to-create-the-project"></a>Создание проекта

1. Запустите Visual Studio.

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. Разверните **Visual Basic** или **Visual C#** и выберите **Windows**.

4. Выберите шаблон проекта **Приложение WPF**.

5. In the **Name** box, type `AdventureWorksProductsEditor` and click **OK**.

     Visual Studio creates the `AdventureWorksProductsEditor` project.

## <a name="create-a-dataset-for-the-application"></a>Create a dataset for the application
 Перед созданием элементов управления с привязкой к данным нужно определить модель данных для своего приложения и добавить ее в окно **Источники данных**. В данном пошаговом руководстве вы создадите набор данных для использования в качестве модели данных.

#### <a name="to-create-a-dataset"></a>Создание набора данных

1. В меню **Данные** выберите команду **Показать источники данных**.

     Открывается окно **Источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных**.

     Открывается **мастер настройки источника данных**.

3. На странице **Выбор типа источника данных** выберите **База данных** и нажмите кнопку **Далее**.

4. На странице **Выбор модели базы данных** выберите **Набор данных** и нажмите кнопку **Далее**.

5. На странице **Выбор подключения к базе данных** выберите один из следующих параметров:

    - Если подключение к учебной базе данных AdventureWorksLT доступно в раскрывающемся списке, то выберите его и нажмите кнопку **Далее**.

    - Щелкните **Создать подключение** и создайте подключение к базе данных AdventureWorksLT.

6. На странице **Сохранение подключения в файле конфигурации приложения** установите флажок **Да, сохранить подключение как** и нажмите кнопку **Далее**.

7. На странице **Выбор объектов базы данных** разверните узел **Таблицы** и выберите таблицу **Продукт (SalesLT)** .

8. Нажмите кнопку **Готово**.

     Visual Studio adds a new AdventureWorksLTDataSet.xsd file to the project, and it adds a corresponding **AdventureWorksLTDataSet** item to the **Data Sources** window. Файл AdventureWorksLTDataSet.xsd определяет типизированный набор данных с именем `AdventureWorksLTDataSet` и адаптер таблицы с именем `ProductTableAdapter`. Позднее в рамках данного пошагового руководства вы воспользуетесь `ProductTableAdapter` для заполнения набора данных данными и сохранения изменений в базу данных.

9. Выполните построение проекта.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edit the default fill method of the TableAdapter
 Чтобы заполнить набор данных данными, используйте метод `Fill` объекта `ProductTableAdapter`. По умолчанию метод `Fill` заполняет `ProductDataTable` в `AdventureWorksLTDataSet` со всеми строками данных из таблицы продукта. Вы можете изменить этот метод, чтобы он возвращал только подмножество строк. В рамках данного руководства измените метод `Fill` для возврата только строк для продуктов с фотографиями.

#### <a name="to-load-product-rows-that-have-photos"></a>Загрузка строк продуктов с фотографиями

1. In **Solution Explorer**, double-click the AdventureWorksLTDataSet.xsd file.

     Открывается Конструктор наборов данных.

2. In the designer, right-click the **Fill,GetData()** query and select **Configure**.

     Открывается **Мастер настройки адаптера таблицы**.

3. На странице **Введите инструкцию SQL** добавьте следующее предложение WHERE после инструкции `SELECT` в текстовом поле.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Нажмите кнопку **Готово**.

## <a name="define-the-user-interface"></a>Define the user interface
 Добавьте несколько кнопок в окно, изменив в XAML в Конструкторе WPF. Позднее в рамках данного пошагового руководства вы добавите код, позволяющий пользователям выполнять прокрутку и сохранять изменения записей продуктов с помощью этих кнопок.

#### <a name="to-define-the-user-interface-of-the-window"></a>Определение пользовательского интерфейса окна

1. In **Solution Explorer**, double-click MainWindow.xaml.

     Открывается окно в Конструкторе WPF.

2. В представлении [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] конструктора добавьте следующий код между тегами `<Grid>`:

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Выполните построение проекта.

## <a name="createdata-bound-controls"></a>Createdata-bound controls
 Create controls that display customer records by dragging the `Product` table from the **Data Sources** window to the WPF Designer.

#### <a name="to-create-data-bound-controls"></a>Порядок создания элементов управления с привязкой к данным

1. В окне **Источники данных** щелкните раскрывающееся меню для узла **Product** и выберите команду **Сведения**.

2. Разверните узел **Product**.

3. Для этого примера некоторые поля не отображаются, поэтому щелкните раскрывающееся меню рядом со следующими узлами и выберите **Нет**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4. Щелкните раскрывающееся меню рядом с узлом **ThumbNailPhoto** и выберите **Изображение**.

    > [!NOTE]
    > По умолчанию у элементов в окне **Источники данных**, представляющих изображения, для элемента управления по умолчанию задано значение **Нет**. Это вызвано тем, что изображения хранятся в базах данных в виде байтовых массивов, которые могут содержать все — от простого массива байтов до исполняемого файла или большого приложения.

5. Из окна **Источники данных** перетащите узел **Product** на строку сетки под строкой с кнопками.

     Visual Studio создает XAML, который определяет набор элементов управления, привязанных к данным в таблице **Products**. Также создается код, который загружает эти данные. For more information about the generated XAML and code, see [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. Щелкните в конструкторе текстовое поле рядом с меткой **Идентификатор продукта**.

7. В окне **Свойства** установите флажок рядом со свойством **IsReadOnly**.

## <a name="navigating-product-records"></a>Navigating product records
 Добавьте код, позволяющий пользователям выполнять прокрутку записей продуктов с помощью кнопок **\<** и **>** .

#### <a name="to-enable-users-to-navigate-product-records"></a>Предоставление пользователям возможности навигации по записям продуктов

1. В конструкторе дважды щелкните кнопку **<** на поверхности окна.

     Visual Studio открывает файл кода программной части и создает обработчик событий `backButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Измените обработчик событий `Window_Loaded`, чтобы `ProductViewSource`, `AdventureWorksLTDataSet` и `AdventureWorksLTDataSetProductTableAdapter` находились за рамками метода и были доступны всей форме. Declare only these to be global to the form, and assign them within the `Window_Loaded` event handler similar to the following:

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. Добавьте следующий код в обработчик событий `backButton_Click` .

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. Вернитесь в конструктор и дважды щелкните кнопку **>** .

5. Добавьте следующий код в обработчик событий `nextButton_Click` .

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>Savechanges to product records
 Добавьте код, позволяющий пользователям сохранять изменения в записях продуктов с помощью кнопки **Сохранить изменения**.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Добавление возможности сохранения изменений в записях продуктов

1. В конструкторе дважды щелкните кнопку **Сохранить изменения**.

     Visual Studio открывает файл кода программной части и создает обработчик событий `saveButton_Click` для события <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Добавьте следующий код в обработчик событий `saveButton_Click` .

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > В этом примере для сохранения изменений используется метод `Save` объекта `TableAdapter`. В данном пошаговом руководстве это целесообразно, так как изменяется только одна таблица данных. Если необходимо сохранить изменения нескольких таблиц, можно воспользоваться методом `UpdateAll` объекта `TableAdapterManager`, который Visual Studio создает вместе с вашим набором данных. For more information, see [TableAdapterManager Overview](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

## <a name="test-the-application"></a>Тестирование приложения
 Выполните сборку и запуск приложения. Убедитесь, что вы можете просмотреть и обновить записи продуктов.

#### <a name="to-test-the-application"></a>Тестирование приложения

1. Нажмите клавишу **F5**.

     Выполняется сборка и запуск приложения. Проверьте следующее.

    - Текстовые поля отображают данные из первой записи продукта с фотографией. Этот продукт имеет идентификатор 713 и имя **Long-Sleeve Logo Jersey, S**.

    - Вы можете нажать кнопку **>** или **<** для перехода по другим записям продуктов.

2. В одной из записей продуктов измените значение **Размер**, а затем нажмите кнопку **Сохранить изменения**.

3. Закройте приложение и перезапустите его, нажав клавишу **F5** в Visual Studio.

4. Перейдите к измененной записи продукта и убедитесь, что изменения сохранены.

5. Закройте приложение.

## <a name="next-steps"></a>Следующие шаги
 После прохождения пошагового руководства вы можете выполнить следующие задачи.

- Узнайте, как использовать окно **Источники данных** в Visual Studio для привязки элементов управления WPF к другим типам источников данных. For more information, see [Bind WPF controls to a WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Узнайте, как использовать окно **Источники данных** в Visual Studio для отображения связанных данных (то есть данных в отношении "родитель — потомок") в элементах управления WPF. For more information, see [Walkthrough: Displaying Related Data in a WPF Application](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>См. также раздел
 [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Dataset tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [WPF and Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) [Data Binding Overview](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
