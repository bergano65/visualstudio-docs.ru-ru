---
title: 'Пошаговое руководство: Получение кэшированных данных из книги на сервере'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b9b9296bd57e7f3057dfbca86c16b1ac41418ba0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Пошаговое руководство: Получение кэшированных данных из книги на сервере
  В этом пошаговом руководстве показано, как извлечь данные из набора данных, который кэшируется в книге Microsoft Office Excel без запуска Excel с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Определение набора данных, содержащий данные из *AdventureWorksLT* базы данных.  
  
-   Создание экземпляров набора данных в проекте книги Excel и проект консольного приложения.  
  
-   Создание <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанные к набору данных в книге и заполнение <xref:Microsoft.Office.Tools.Excel.ListObject> данными при открытии книги.  
  
-   Добавление набора данных в книге для кэширования данных.  
  
-   Чтение данных из кэшированного набора данных в набор данных в консольном приложении без запуска Excel.  
  
 Несмотря на то, что в данном пошаговом руководстве предполагается, что код выполняется на компьютере разработчика, рассмотренные в этом пошаговом руководстве код можно использовать на сервере, на котором не установлен Excel.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Доступ к запущенному экземпляру Microsoft SQL Server или Microsoft SQL Server Express с подключенной учебной базой данных AdventureWorksLT, присоединенные к нему. Можно загрузить базу данных AdventureWorksLT с [веб-сайта CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Дополнительные сведения о подключении базы данных см. в следующих разделах:  
  
    -   Присоединение базы данных с помощью SQL Server Management Studio или SQL Server Management Studio Express, в разделе [как: присоединение базы данных (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Присоединение базы данных с помощью командной строки, в разделе [как: прикрепить файл базы данных SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Создайте проект библиотеки классов, который определяет набор данных  
 Чтобы использовать тот же набор данных в проекте книги Excel и в консольном приложении, необходимо определить набор данных в отдельной сборке, на которую ссылается оба проекта. В этом пошаговом руководстве необходимо определите набор данных в проекте библиотеки классов.  
  
#### <a name="create-the-class-library-project"></a>Создание проекта для библиотеки классов  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем нажмите кнопку **Windows**.  
  
4.  В списке шаблонов проектов выберите **библиотеки классов**.  
  
5.  В **имя** введите **AdventureWorksDataSet**.  
  
6.  Нажмите кнопку **Обзор**, перейдите к *%UserProfile%\My документов* (для Windows XP и более ранних версий) или *%UserProfile%\Documents* (для Windows Vista) папки, а затем нажмите кнопку **Выберите папку**.  
  
7.  В **новый проект** диалогового окна убедитесь, что **создать каталог для решения** флажок не установлен.  
  
8.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **AdventureWorksDataSet** проекта **обозревателе решений** и открывает *Class1.cs* или *Class1.vb* файл кода.  
  
9. В **обозревателе решений**, щелкните правой кнопкой мыши *Class1.cs* или *Class1.vb*, а затем нажмите кнопку **удалить**. Этот файл не обязательно для данного пошагового руководства.  
  
## <a name="define-a-dataset-in-the-class-library-project"></a>Определить набор данных в проекте библиотеки классов  
 Определите типизированный набор данных, содержащий данные из базы данных AdventureWorksLT для SQL Server 2005. Далее в этом пошаговом руководстве будет ссылаться этот набор данных в проекте книги Excel и проект консольного приложения.  
  
 Набор данных является *типизированным набором данных* , представляющий данные в таблице Product базы данных AdventureWorksLT. Дополнительные сведения о типизированных наборах данных см. в разделе [средства набора данных в Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Определение типизированного набора данных в проекте библиотеки классов  
  
1.  В **обозревателе решений**, нажмите кнопку **AdventureWorksDataSet** проекта.  
  
2.  Если **источники данных** окно не отображается, откройте его в строке меню, выберите **представление** > **другие окна**  >   **Источники данных**.  
  
3.  Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.  
  
4.  Щелкните **База данных**и нажмите кнопку **Далее**.  
  
5.  Если имеется существующее подключение к базе данных AdventureWorksLT, выберите его и нажмите кнопку **Далее**.  
  
     В противном случае нажмите **Создать подключение**и в диалоговом окне **Добавление подключения** создайте новое подключение. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
6.  На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.  
  
7.  В **Выбор объектов базы данных** разверните **таблиц** и выберите **продукт (SalesLT)**.  
  
8.  Нажмите кнопку **Готово**.  
  
     *AdventureWorksLTDataSet.xsd* добавляется файл **AdventureWorksDataSet** проекта. В этом файле определены следующие элементы:  
  
    -   Типизированный набор данных с именем `AdventureWorksLTDataSet`. Этот набор данных представляет содержимое таблицы Product в базе данных AdventureWorksLT.  
  
    -   Адаптер таблицы с именем `ProductTableAdapter`. Этот адаптер таблицы можно использовать для чтения и записи данных `AdventureWorksLTDataSet`. Дополнительные сведения см. в разделе [Общие сведения о TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Далее в пошаговом руководстве используются оба эти объекта.  
  
9. В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksDataSet** и нажмите кнопку **сборки**.  
  
     Убедитесь, что сборка проекта выполняется без ошибок.  
  
## <a name="create-an-excel-workbook-project"></a>Создайте проект книги Excel  
 Создайте проект книги Excel для интерфейса к данным. Далее в этом пошаговом руководстве вы создадите <xref:Microsoft.Office.Tools.Excel.ListObject> , отображающий данные и позволит добавить экземпляр набора данных в кэш данных в книге.  
  
#### <a name="create-the-excel-workbook-project"></a>Создание проекта книги Excel  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksDataSet** решений, выберите пункт **добавить**, а затем нажмите кнопку **новый проект**.  
  
2.  В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.  
  
3.  В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .  
  
4.  В списке шаблонов проектов выберите проект **Книга Excel 2010** или **Книга Excel 2013** .  
  
5.  В **имя** введите **AdventureWorksReport**. Не изменяйте расположение.  
  
6.  Нажмите кнопку **ОК**.  
  
     Откроется **Мастер проектов набора средств Visual Studio для Office** .  
  
7.  Убедитесь, что **создания документа** установлен и нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает **AdventureWorksReport** книгу в конструкторе и добавляет **AdventureWorksReport** проекта **обозревателе решений**.  
  
## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Добавление набора данных к источникам данных в проекте книги Excel  
 Перед отображением набора данных в книге Excel, необходимо сначала добавить набор данных к источникам данных в проекте книги Excel.  
  
1.  В **обозревателе решений**, дважды щелкните *Sheet1.cs* или *Sheet1.vb* под **AdventureWorksReport** проекта.  
  
     Книга откроется в конструкторе.  
  
2.  В меню **Данные** выберите команду **Добавить новый источник данных**.  
  
     **Мастер настройки источника данных** открывается.  
  
3.  Нажмите кнопку **объекта**, а затем нажмите кнопку **Далее**.  
  
4.  В **Выбор объекта для привязки** для щелкните **добавить ссылку**.  
  
5.  На **проекты** щелкните **AdventureWorksDataSet** и нажмите кнопку **ОК**.  
  
6.  В разделе **AdventureWorksDataSet** пространство имен **AdventureWorksDataSet** сборки, нажмите кнопку **AdventureWorksLTDataSet** и нажмите кнопку **Готово** .  
  
     **Источники данных** откроется окно, и **AdventureWorksLTDataSet** добавляется в список источников данных.  
  
## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Создайте элемент управления ListObject, привязанного к экземпляру набора данных  
 Чтобы отобразить набор данных в книге, создайте <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанную к экземпляру набора данных. Дополнительные сведения о привязке элементов управления к данным см. в разделе [привязывать данные к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
1.  В **источники данных** окна, разверните **AdventureWorksLTDataSet** узле **AdventureWorksDataSet**.  
  
2.  Выберите **продукта** узел, щелкните стрелку раскрывающегося списка и выберите **ListObject** в раскрывающемся списке.  
  
     Если стрелку раскрывающегося списка не отображается, убедитесь, что книга открыта в конструкторе.  
  
3.  Перетащите **продукта** таблицы в ячейку A1.  
  
     Объект <xref:Microsoft.Office.Tools.Excel.ListObject> управления с именем `productListObject` создается на листе с началом в ячейку A1. В то же время, объект dataset с именем `adventureWorksLTDataSet` и <xref:System.Windows.Forms.BindingSource> с именем `productBindingSource` добавляются в проект. Объект <xref:Microsoft.Office.Tools.Excel.ListObject> привязан к объекту <xref:System.Windows.Forms.BindingSource>, который в свою очередь привязан к объекту набора данных.  
  
## <a name="add-the-dataset-to-the-data-cache"></a>Добавьте набор данных в кэше данных  
 Чтобы включить кода за пределами проекта книги Excel, доступ к набору данных в книге, необходимо добавить набор данных в кэше данных. Дополнительные сведения о кэше данных см. в разделе [кэшированных данных в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md) и [данные кэша](../vsto/caching-data.md).  
  
1.  В конструкторе щелкните **adventureWorksLTDataSet**.  
  
2.  В **свойства** задайте **модификаторы** свойства **открытый**.  
  
3.  Задать **CacheInDocument** свойства **True**.  
  
## <a name="initialize-the-dataset-in-the-workbook"></a>Инициализации набора данных в книге  
 Прежде чем можно получить данные из кэшированного набора данных с помощью консольного приложения, необходимо заполнить кэшированный набор данных с данными.  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши *Sheet1.cs* или *Sheet1.vb* файла и нажмите кнопку **Просмотр кода**.  
  
2.  Замените обработчик событий `Sheet1_Startup` следующим кодом. Этот код использует экземпляр `ProductTableAdapter` класс, который определен в **AdventureWorksDataSet** проекта для заполнения кэшированный набор данных данными, если он пуст.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 Постройте и запустите проект книги Excel, чтобы убедиться, что он компилируется и выполняется без ошибок. Эта операция также заполняет набор и сохраняет данные в книге.  
  
#### <a name="build-and-run-the-project"></a>Построение и запуск проекта  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksReport** проекта, выбор **отладки**, а затем нажмите кнопку **запустить новый экземпляр**.  
  
     Построение проекта, а книга будет открыта в Excel. Проверьте следующее.  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> Заполняется данными.  
  
    -   Значение в **ListPrice** столбца для первой строки <xref:Microsoft.Office.Tools.Excel.ListObject> равно 1431,5. Далее в этом пошаговом руководстве используется консольное приложение для изменения значений во **ListPrice** столбца.  
  
2.  Сохраните книгу. Не изменяйте имя файла или расположение книги.  
  
3.  Закройте Excel.  
  
## <a name="create-a-console-application-project"></a>Создайте проект консольного приложения  
 Создайте проект консольного приложения, чтобы использовать для изменения данных в кэшированный набор данных в книге.  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksDataSet** решений, выберите пункт **добавить**, а затем нажмите кнопку **новый проект**.  
  
2.  В **типы проектов** области, разверните **Visual C#** или **Visual Basic**, а затем нажмите кнопку **Windows**.  
  
3.  В **шаблоны** выберите **консольное приложение**.  
  
4.  В **имя** введите **DataReader**. Не изменяйте расположение.  
  
5.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **DataReader** проекта **обозревателе решений** и открывает *Program.cs* или *Module1.vb* файл кода.  
  
## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Извлечение данных из кэшированного набора данных с помощью консольного приложения  
 Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса в консольное приложение для чтения данных в локальный `AdventureWorksLTDataSet` объекта. Чтобы убедиться, что локальный набор данных данных инициализирован с помощью кэшированного набора данных, приложение отображает число строк в локальном наборе данных.  
  
#### <a name="retrieve-data-from-the-cached-dataset"></a>Получить данные из кэшированного набора данных  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **DataReader** проекта и нажмите кнопку **добавить ссылку**.  
  
2.  На **.NET** выберите Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
3.  Нажмите кнопку **ОК**.  
  
4.  В **обозревателе решений**, щелкните правой кнопкой мыши **DataReader** проекта и нажмите кнопку **добавить ссылку**.  
  
5.  На **проекты** выберите **AdventureWorksDataSet**и нажмите кнопку **ОК**.  
  
6.  Откройте *Program.cs* или *Module1.vb* файл в редакторе кода.  
  
7.  Добавьте следующие **с помощью** (для C#) или **Imports** (для Visual Basic) в начало файла кода.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Добавьте следующий код в метод `Main` . Этот код объявляет следующие объекты:  
  
    -   Экземпляр `AdventureWorksLTDataSet` типа, определенного в **AdventureWorksDataSet** проекта.  
  
    -   Путь к книге AdventureWorksReport в папке построения **AdventureWorksReport** проекта.  
  
    -   Объект <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> объект, используемый для доступа к кэшу данных в книге.  
  
        > [!NOTE]  
        >  В следующем коде предполагается, что книга сохраняется с помощью *.xlsx* расширения. Если книга в проекте имеет другое расширение, измените путь соответственно.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Добавьте следующий код в `Main` метод после кода, добавленного на предыдущем шаге. Этот код выполняет следующие задачи:  
  
    -   Она использует <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса для доступа к кэшированный набор данных в книге.  
  
    -   Он считывает данные из кэшированного набора данных в локальный набор данных.  
  
    -   Выводит количество строк в локальном наборе данных, убедитесь, что он содержит данные.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. На **построения** меню, нажмите кнопку **Построить DataReader**.  
  
## <a name="test-the-project"></a>Тестирование проекта  
 При запуске консольного приложения отображается число строк в локальном наборе данных.  
  
#### <a name="test-the-workbook"></a>Тестирование книги  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **DataReader** проект, выберите пункт **отладки**, а затем нажмите кнопку **запустить новый экземпляр**.  
  
     Убедитесь, что приложение сообщает, локальный набор данных состоит из строк 295.  
  
2.  Нажмите клавишу **ввод** закрыть приложение.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о работе с кэшированными данными в следующих разделах:  
  
-   Изменение данных в кэшированный набор данных без запуска Excel. Дополнительные сведения см. в разделе [Пошаговое руководство: изменение кэшированных данных в книгу на сервере](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Вставка данных в книгу на сервере](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Пошаговое руководство: Изменение кэшированных данных в книгу на сервере](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
  
  