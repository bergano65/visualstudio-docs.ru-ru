---
title: 'Пошаговое руководство: Создание адаптера таблицы с несколькими запросами | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564064"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Пошаговое руководство. Создание адаптера таблицы с несколькими запросами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы создадите адаптер таблицы в наборе данных с помощью [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Пошаговое руководство помогает выполнить процесс создания второго запроса в [TableAdapter](../data-tools/tableadapter-overview.md) с помощью [редактирования TableAdapters](../data-tools/editing-tableadapters.md) в [конструктор наборов данных](../data-tools/creating-and-editing-typed-datasets.md).  
  
 В данном пошаговом руководстве представлены следующие задачи.  
  
-   Создание нового **приложения Windows** проекта.  
  
-   Создание и настройка источника данных в приложении путем создания набора данных с помощью **мастер настройки источника данных**.  
  
-   Открытие нового набора данных в **конструктор наборов данных**.  
  
-   Добавление запросов в адаптер таблицы с **мастер настройки запроса TableAdapter**.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к учебной базе данных "Борей" (версия SQL Server или Access). Дополнительные сведения см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Создание нового приложения Windows  
 Первым шагом является создание приложения Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Порядок создания нового проекта приложения Windows  
  
1.  В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], из **файл** меню, создайте новый проект.  
  
2.  Выберите язык программирования в **типы проектов** области.  
  
3.  Нажмите кнопку **приложения Windows** в **шаблоны** области.  
  
4.  Назовите проект `TableAdapterQueriesWalkthrough`, а затем нажмите кнопку **ОК**.  
  
     Visual Studio добавит проект в **обозревателе решений** и отображает новую форму в конструкторе.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Создание источника данных в виде базы данных с помощью адаптера таблицы  
 На этом шаге создается источник данных с помощью **мастер настройки источника данных** на основе `Customers` таблицы в базе данных Northwind. Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения о настройке учебной базе данных Northwind, см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  В меню **Данные** выберите команду **Показать источники данных**.  
  
2.  В **источников данных** выберите **добавить новый источник данных** запустить **мастер настройки источника данных**.  
  
3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.  
  
4.  На **Выбор подключения базы данных** странице выполните одно из следующих:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         - или -  
  
    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.  
  
5.  Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.  
  
6.  Нажмите кнопку **Далее** на **сохранение подключения в файле конфигурации приложения** страницы.  
  
7.  Разверните **таблиц** узел на **Выбор объектов базы данных** страницы.  
  
8.  Выберите **клиентов** таблицы, а затем нажмите кнопку **Готово**.  
  
     **NorthwindDataSet** добавляется в проект и **клиентов** таблица появится в **источников данных** окна.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Открытие набора данных в Конструкторе наборов данных  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Порядок открытия набора данных в Конструкторе наборов данных  
  
1.  Щелкните правой кнопкой мыши **NorthwindDataset** в **источников данных** окна.  
  
2.  В контекстном меню выберите **изменить набор данных с помощью конструктора**.  
  
     NorthwindDataset открывается в **конструктор наборов данных**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Добавление второго запроса в CustomersTableAdapter  
 Мастер создал набор данных с помощью **клиентов** таблицы данных и **CustomersTableAdapter**. В этом разделе пошагового руководства осуществляется добавление второго запроса к **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>Порядок добавления запроса в CustomersTableAdapter  
  
1.  Перетащите **запроса** из **набора данных** вкладке **элементов** на **клиентов** таблицы.  
  
     [Редактирования TableAdapters](../data-tools/editing-tableadapters.md) открывает.  
  
2.  Выберите **использовать инструкции SQL**, а затем нажмите кнопку **Далее**.  
  
3.  Выберите **SELECT, возвращающая строки**, а затем нажмите кнопку **Далее**.  
  
4.  Добавьте в запрос предложение WHERE, чтобы он имел следующий вид:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Если вы используете версию доступа Northwind, замените @City параметр с вопросительным знаком. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  На **Выбор методов для создания** странице, назовите **Заполнение DataTable** метод `FillByCity`.  
  
    > [!NOTE]
    >  Метод **возвращение DataTable** не используется в этом пошаговом руководстве, поэтому можно снять флажок или оставить имя по умолчанию.  
  
6.  Нажмите кнопку **Далее** и завершите работу мастера.  
  
     **FillByCity** запрос добавляется **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Добавление кода для выполнения дополнительного запроса на форме  
  
#### <a name="to-execute-the-query"></a>Порядок выполнения запроса  
  
1.  Выберите **Form1** в **обозревателе решений**и нажмите кнопку **конструктор представлений**.  
  
2.  Перетащите **клиентов** узел из **источников данных** окно, чтобы **Form1**.  
  
3.  Переключитесь в представление кода, выбрав **кода** из **представление** меню.  
  
4.  Замените код в обработчике событий `Form1_Load` на следующий код для выполнения запроса `FillByCity`:  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
-   Нажмите клавишу F5.  
  
-   Сетка заполняется клиентами, у которых `City` имеет значение `Seattle`.  
  
## <a name="next-steps"></a>Следующие шаги  
  
### <a name="to-add-functionality-to-your-application"></a>Добавление функциональности в приложение  
  
-   Добавьте элементы управления <xref:System.Windows.Forms.TextBox> и <xref:System.Windows.Forms.Button> и передайте значение из текстового поля в запрос. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Добавьте логику проверки данных в событие <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> таблиц данных в наборе данных. Дополнительные сведения см. в разделе [проверки данных в наборах данных](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md)   
 [Практическое: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)