---
title: 'Пошаговое руководство: Создание службы данных WCF с WPF и Entity Framework'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1433620303c8bf300645681eeabcd12c4a9c36d7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Пошаговое руководство: Создание службы данных WCF с WPF и Entity Framework
В этом пошаговом руководстве демонстрируется создание простой [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , размещенном в [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] веб-приложения и последующий доступ к ней из приложения Windows Forms.

В этом пошаговом руководстве:

-   Создайте веб-приложение, размещаемое в [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Будет создана [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], представляющая таблицу Customers в базе данных Northwind.

-   Создайте таблицу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Создайте клиентское приложение и добавьте ссылку на [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Будет включена привязка данных к службе и создан пользовательский интерфейс.

-   При необходимости в приложение будут добавлены возможности фильтрации.

## <a name="prerequisites"></a>Предварительные требования
В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **хранения и обработки данных** рабочей нагрузки, или в отдельных компонентов.

2.  Установка образца базы данных Northwind, выполните следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на экземпляре LocalDB и выберите **нового запроса...** .

       Откроется окно редактора запросов.

    2. Копировать [сценарий Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот скрипт T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время завершения выполнения запроса и создания базы данных "Борей".

## <a name="creating-the-service"></a>Создание службы
Чтобы создать службу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], необходимо добавить веб-проект, создать [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] и службу из модели.

Сначала добавляется веб-проект для размещения службы.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-the-web-project"></a>Создание веб-проекта

1.  В строке меню выберите **файл**, **New**, **проекта**.

2.  В **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#** и **Web** узлов и нажмите кнопку **ASP. Веб-приложения NET** шаблона.

3.  В **имя** текста введите **NorthwindWeb**, а затем выберите **ОК** кнопки.

4.  В **новый проект ASP.NET** в диалоговом **выберите шаблон** выберите **пустой**, а затем выберите **ОК** кнопки.

На следующем шаге вы создадите [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] , представляющая таблицу Customers в базе данных Northwind.

#### <a name="to-create-the-entity-data-model"></a>Создание модели EDM

1.  В строке меню выберите **проекта**, **Добавление нового элемента**.

2.  В **Добавление нового элемента** диалогового окна выберите **данные** узел и выберите **ADO.NET Entity Data Model** элемента.

3.  В **имя** текста введите `NorthwindModel`, а затем выберите **добавить** кнопки.

     Появится мастер модели EDM.

4.  В мастере модель данных сущности на **Выбор содержимого модели** выберите **конструктор EF из базы данных** элемента, а затем выберите **Далее** кнопки.

5.  На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         - или -

    -   Выберите **новое подключение** кнопку, чтобы настроить новое подключение к данным. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).

6.  Если базе данных требуется пароль, выберите **Да, включить конфиденциальные данные в строке подключения** переключатель, а затем выберите **Далее** кнопки.

    > [!NOTE]
    >  Если отображается диалоговое окно, нажмите **Да** для сохранения файла в проект.

7.  На **Выбор версии** выберите **Entity Framework 5.0** переключатель, а затем выберите **Далее** кнопки.

    > [!NOTE]
    >  Чтобы использовать последнюю версию Entity Framework 6 со службами WCF, необходимо установить пакет WCF Data Services Entity Framework Provider NuGet. В разделе [использование WCF Data Services 5.6.0 с Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).

8.  На **Выбор объектов базы данных** разверните **таблиц** выберите **клиентов** флажок и нажмите кнопку **Готово** кнопка.

     Будет отображена диаграмма модели сущности, и файл NorthwindModel.edmx будет добавлен в проект.

На следующем шаге будет создавать и тестировать службу данных.

#### <a name="to-create-the-data-service"></a>Создание службы данных

1.  В строке меню выберите **проекта**, **Добавление нового элемента**.

2.  В **Добавление нового элемента** диалогового окна выберите **Web** узел и выберите **служба данных WCF 5.6** элемента.

3.  В **имя** текста введите `NorthwindCustomers`, а затем выберите **добавить** кнопки.

     Файл NorthwindCustomers.svc появится в **редактор кода**.

4.  В **редактор кода**, найдите первый `TODO:` комментирования и замените код следующим:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5.  Замените комментарии в обработчике событий `InitializeService` следующим кодом:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6.  В строке меню выберите **отладки**, **Запуск без отладки** для запуска службы. Откроется окно браузера, и в нем будет отображена схема XML для службы.

7.  В **адрес** введите `Customers` в конце URL-адрес для файла NorthwindCustomers.svc, а затем выберите **ввод** ключа.

     Будет отображено XML-представление данных в таблице Customers.

    > [!NOTE]
    >  В некоторых случаях обозреватель Internet Explorer может неправильно интерпретировать данные как RSS-канал. Необходимо убедиться, что параметр, определяющий, отображаются ли RSS-каналы, отключен. Дополнительные сведения см. в разделе [Устранение неполадок ссылок на службы](../data-tools/troubleshooting-service-references.md).

8.  Закройте окно браузера.

В ходе следующих этапов будет создано клиентское приложение Windows Forms для использования службы.

## <a name="creating-the-client-application"></a>Создание клиентского приложения
 Чтобы создать клиентское приложение, потребуется добавить второй проект, добавить к проекту ссылку на службу, настроить источник данных и создать пользовательский интерфейс, отображающий данные из службы.

 Сначала проект Windows Forms добавляется к решению и устанавливается как загружаемый проект.

#### <a name="to-create-the-client-application"></a>Создание клиентского приложения

1.  В строке меню выберите файл **добавить**, **новый проект**.

2.  В **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#** узел и выберите **Windows** узел и нажмите кнопку  **Приложения Windows Forms в**.

3.  В текстовом поле **Имя** введите `NorthwindClient` и нажмите кнопку **ОК**.

4.  В **обозревателе решений**, выберите **NorthwindClient** узел проекта.

5.  В строке меню выберите **проекта**, **Назначить запускаемым проектом**.

На следующем шаге вы добавите ссылку на службу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] веб-проекта.

#### <a name="to-add-a-service-reference"></a>Добавление ссылки на службу

1.  В строке меню выберите **проекта**, **добавить ссылку на службу**.

2.  В **добавить ссылку на службу** диалогового окна выберите **Discover** кнопки.

     URL-адрес службы NorthwindCustomers отображается в **адрес** поля.

3.  Выберите **ОК** кнопку, чтобы добавить ссылку на службу.

На следующем шаге вы настроите источника данных для обеспечения привязки данных к службе.

#### <a name="to-enable-data-binding-to-the-service"></a>Включение привязки данных к службе

1.  В строке меню выберите **представление**, **другие окна**, **источники данных**.

2.  В **источники данных** окно, выберите **добавить новый источник данных** кнопки.

3.  На **Выбор типа источника данных** страница **мастер настройки источника данных**, выберите **объекта**и нажмите кнопку **Далее** кнопки .

4.  На **Выбор объектов данных** разверните **NorthwindClient** узел, а затем разверните **NorthwindClient.ServiceReference1** узла.

5.  Выберите **клиента** флажок и нажмите кнопку **Готово** кнопки.

На следующем шаге вы создадите пользовательский интерфейс, который будет отображать данные из службы.

#### <a name="to-create-the-user-interface"></a>Создание пользовательского интерфейса

1.  В **источники данных** окна, откройте контекстное меню для **клиентов** узел и выберите **копирования**.

2.  В **Form1.vb** или **Form1.cs** конструкторе форм, откройте контекстное меню и выберите **вставить**.

     На форму добавится элемент управления <xref:System.Windows.Forms.DataGridView>, компонент <xref:System.Windows.Forms.BindingSource> и компонент <xref:System.Windows.Forms.BindingNavigator>.

3.  Выберите **CustomersDataGridView** управления, а затем в **свойства** задайте **Dock** свойства **заполнения**.

4.  В **обозревателе решений**, откройте контекстное меню для **Form1** узел и выберите **Просмотр кода** чтобы открыть редактор кода и добавьте следующие операторы Imports или Using в начало файла:

    ```vb
    Imports NorthwindClient.ServiceReference1
    ```

    ```csharp
    using NorthwindClient.ServiceReference1;
    ```

5.  Добавьте следующий код в обработчик событий `Form1_Load`.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
            Dim proxy As New NorthwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
            Me.CustomersBindingSource.DataSource = proxy.Customers
        End Sub
    ```

    ```csharp
    private void Form1_Load(object sender, EventArgs e)
    {
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
    this.CustomersBindingSource.DataSource = proxy.Customers;
    }

    ```

6.  В **обозревателе решений**, откройте контекстное меню файла NorthwindCustomers.svc и выберите **Просмотр в браузере**. Откроется Internet Explorer, и в нем будет отображена схема XML для службы.

7.  Скопируйте URL-адрес из адресной строки обозревателя Internet Explorer.

8.  В коде, добавленном на этапе 4, выберите код `http://localhost:53161/NorthwindCustomers.svc/` и замените его только что скопированным URL-адресом.

9. В строке меню выберите **отладки**, **начать отладку** для запуска приложения. Будут отображены сведения о клиенте.

 Теперь в наличии имеется рабочее приложение, которое будет отображать список клиентов из службы NorthwindCustomers. При необходимости в отображении дополнительных данных посредством службы, свойство [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] можно изменить, чтобы включить дополнительные таблицы из базы данных Northwind.

Следующим необязательным этапом является изучение фильтрации данных, возвращаемых службой.

## <a name="adding-filtering-capabilities"></a>Добавление возможностей фильтрации
 На данном этапе будет выполнена настройка приложения на фильтрацию данных по городу клиента.

#### <a name="to-add-filtering-by-city"></a>Добавление фильтрации по городу

1.  В **обозревателе решений**, откройте контекстное меню для **Form1.vb** или **Form1.cs** узел и выберите **откройте**.

2.  Добавить <xref:System.Windows.Forms.TextBox> управления и <xref:System.Windows.Forms.Button> управления из **элементов** в форму.

3.  Откройте контекстное меню для <xref:System.Windows.Forms.Button> управления и выберите **Просмотр кода**и затем добавьте следующий код в `Button1_Click` обработчик событий:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4.  В коде выше замените `http://localhost:53161/NorthwindCustomers.svc` URL-адресом из обработчика событий `Form1_Load`.

5.  В строке меню выберите **отладки**, **начать отладку** для запуска приложения.

6.  В текстовом поле введите **Лондоне**, а затем нажмите кнопку. Будут отображены только клиенты из Лондона.

## <a name="see-also"></a>См. также

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Практическое руководство. Добавление, обновление или удаление ссылки на службу данных WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)