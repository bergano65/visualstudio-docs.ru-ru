---
title: "Пошаговое руководство: Создание отношения подробности Master с помощью кэшированного набора данных | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 161fdc5e35a24b1318a44d2102867961330ba559
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>Пошаговое руководство: Создание отношения подробности Master с помощью кэшированного набора данных
  В этом пошаговом руководстве демонстрируется создание иерархического отношения на листе и кэширование данных, решения можно использовать в автономном режиме.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Добавление элементов управления на лист.  
  
-   Настройка набора данных должен быть кэширован на листе.  
  
-   Добавьте код, чтобы включить прокрутку записей.  
  
-   Тестирование проекта.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Доступ к учебной базе данных "Борей" SQL Server. База данных может быть на компьютере разработчика или на сервере.  
  
-   Разрешения на чтение и запись в базу данных SQL Server.  
  
## <a name="creating-a-new-project"></a>Создание нового проекта  
 На этом шаге вы создадите проект книги Excel.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект книги Excel с именем **Мой основной-подробности**, с помощью Visual Basic или C#. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio открывает новую книгу Excel в конструкторе и добавляет **Мой основной-подробности** проекта **обозревателе решений**.  
  
## <a name="creating-the-data-source"></a>Создание источника данных  
 С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  Если окно **Источники данных** не отображается, откройте его, выбрав в строке меню пункты **Вид**, **Другие окна**, **Источники данных**.  
  
2.  Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.  
  
3.  Выберите **базы данных** и нажмите кнопку **Далее**.  
  
4.  Выберите подключение данных к базе данных Northwind SQL Server или добавьте новое подключение с помощью **новое подключение** кнопки.  
  
5.  После выбора или создания подключения нажмите кнопку **Далее**.  
  
6.  Удалить параметр, чтобы сохранить подключение, если он установлен, а затем щелкните **Далее**.  
  
7.  Разверните **таблиц** узел в **объектов базы данных** окна.  
  
8.  Выберите **заказов** таблицы и **Order Details** таблицы.  
  
9. Нажмите кнопку **Готово**.  
  
 Мастер добавляет две таблицы для **источники данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Добавление элементов управления на лист  
 На этом шаге вы добавите именованного диапазона, объекта списка и две кнопки на первый лист. Сначала добавьте именованный диапазон и объект списка из **источники данных** окна, чтобы они автоматически привязываются к источнику данных. Добавьте кнопки, из **элементов**.  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>Добавление именованного диапазона и объекта списка  
  
1.  Убедитесь, что **Мои Master-Detail.xlsx** книга открыта в конструкторе Visual Studio с **Sheet1** отображается.  
  
2.  Откройте **источники данных** окна и разверните **заказов** узла.  
  
3.  Выберите **OrderID** столбца и щелкните стрелку раскрывающегося списка, которая появляется.  
  
4.  Нажмите кнопку **NamedRange** в раскрывающемся списке, а затем перетащите **OrderID** столбца в ячейку **A2**.  
  
     Объект <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `OrderIDNamedRange` создается в ячейке **A2**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `OrdersBindingSource`, адаптер таблиц и <xref:System.Data.DataSet> экземпляр добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.  
  
5.  Прокрутите столбцы, которые находятся под **заказов** таблицы. В нижней части списка — **Order Details** таблицы; именно здесь, так как он является дочерним элементом **заказов** таблицы. Выберите этот параметр, **Order Details** таблицы не того, который находится на том же уровне, как **заказов** таблицы, а затем щелкните стрелку раскрывающегося списка, которая появляется.  
  
6.  Нажмите кнопку **ListObject** в раскрывающемся списке, а затем перетащите **OrderDetails** таблицы ячейку **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления с именем **Order_DetailsListObject** создается в ячейке **A6**, а к <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-two-buttons"></a>Добавление двух кнопок  
  
1.  Из **стандартные элементы управления** вкладке **элементов**, добавьте <xref:System.Windows.Forms.Button> управления ячейку **A3** листа.  
  
     Эта кнопка называется `Button1`.  
  
2.  Добавьте еще один <xref:System.Windows.Forms.Button> управления ячейку **B3** листа.  
  
     Эта кнопка называется `Button2`.  
  
 Затем пометьте набор данных должен быть кэширован в документе.  
  
## <a name="caching-the-dataset"></a>Кэширование набора данных  
 Пометить набор данных должен быть кэширован в документе, делая набора данных, открытые и задание **CacheInDocument** свойство.  
  
#### <a name="to-cache-the-dataset"></a>Для кэширования набора данных  
  
1.  Выберите **NorthwindDataSet** в области компонентов.  
  
2.  В **свойства** измените **модификаторы** свойства **открытый**.  
  
     Наборы данных должны быть открытыми, прежде чем включено кэширование.  
  
3.  Изменение **CacheInDocument** свойства **True**.  
  
 Следующий шаг — добавить текст для кнопок, а в C# добавьте код для подключения обработчиков событий.  
  
## <a name="initializing-the-controls"></a>Инициализация элементов управления  
 Задать текст кнопки и добавьте обработчики событий <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> событий.  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>Для инициализации данных и элементов управления  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1.vb** или **Sheet1.cs**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Добавьте следующий код в `Sheet1_Startup` метод, чтобы задать текст для кнопок.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Только в C#, добавьте обработчики событий для кнопки события click `Sheet1_Startup` метод.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Добавление кода, чтобы включить прокрутку записей  
 Добавьте код для <xref:System.Windows.Forms.Control.Click> обработчик событий для каждой кнопки для перемещения по записям.  
  
#### <a name="to-scroll-through-the-records"></a>Прокрутка записей  
  
1.  Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button1`и добавьте следующий код для перемещения по записям в обратном направлении:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button2`и добавьте следующий код, перемещаться по записям:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно протестировать книгу, чтобы убедиться в том, что данные отображаются должным образом и можно использовать решение вне сети.  
  
#### <a name="to-test-the-data-caching"></a>Тестирование кэширования данных  
  
1.  Нажмите клавишу **F5**.  
  
2.  Убедитесь, что именованный диапазон и объект списка заполняются данными из источника данных.  
  
3.  Выполните прокрутку записей, нажимая кнопки.  
  
4.  Сохраните книгу, а затем закройте книгу и Visual Studio.  
  
5.  Отключите подключение к базе данных. Отключите сетевой кабель с компьютера, если база данных расположена на сервере или остановить службу SQL Server, если база данных находится на компьютере разработчика.  
  
6.  Откройте Excel, а затем **Мои Master-Detail.xlsx** из каталога \bin (\My Master-Detail\bin в Visual Basic или \My Master-Detail\bin\debug в C#).  
  
7.  Выполните прокрутку записей, чтобы увидеть, что лист работает в обычном режиме при отключении.  
  
8.  Подключитесь к базе данных. Снова подключить компьютер сети, если база данных расположена на сервере, или запустите службы SQL Server, если база данных находится на компьютере разработчика.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы создания связи главного и подчиненного представлений данных на листе и кэширование набора данных. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Развертывание решения. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Данные в решениях Office](../vsto/data-in-office-solutions.md)   
 [Кэширование данных](../vsto/caching-data.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  