---
title: "Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data services in Visual Studio"
  - "WCF Data Services, Visual Studio"
  - "ADO.NET Data Services, Visual Studio"
  - "WCF data services in Visual Studio"
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio
В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] в веб\-приложении [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и последующий доступ к ней из приложения Windows Forms.  
  
 В этом пошаговом руководстве:  
  
-   Создайте веб\-приложение, размещаемое в [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Будет создана [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], представляющая таблицу Customers в базе данных Northwind.  
  
-   Создайте таблицу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Создайте клиентское приложение и добавьте ссылку на [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Будет включена привязка данных к службе и создан пользовательский интерфейс.  
  
-   При необходимости в приложение будут добавлены возможности фильтрации.  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Наличие учебной базы данных Northwind.  
  
     Если этой базы данных нет на компьютере разработки, ее можно загрузить в [Центре загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=98088).  Инструкции см. в разделе [Загрузка образцов баз данных](../Topic/Downloading%20Sample%20Databases.md).  
  
## Создание службы  
 Чтобы создать службу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], необходимо добавить веб\-проект, создать [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] и службу из модели.  
  
 Сначала добавляется веб\-проект для размещения службы.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Создание веб\-проекта  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C\#** и выберите пункт **Веб**, а затем выберите шаблон **Веб\-приложение ASP.NET**.  
  
3.  В текстовом поле **Имя** введите NorthwindWeb и нажмите кнопку **ОК**.  
  
4.  В диалоговом окне **Новый проект ASP.NET** в списке **Выбор шаблона** выберите **Пустой**, а затем нажмите кнопку **ОК**.  
  
 На данном этапе будет создана [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], представляющая таблицу Customers в базе данных Northwind.  
  
#### Создание модели EDM  
  
1.  В строке меню выберите **Проект**, **Добавить новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите узел **Данные** и выберите элемент **Модель EDM ADO.NET**.  
  
3.  В поле **Имя** введите `NorthwindModel` и нажмите кнопку **Добавить**.  
  
     Появится мастер модели EDM.  
  
4.  В мастере моделей EDM на странице **Выбор модели содержимого** выберите элемент **Конструктор EF из базы данных** и нажмите кнопку **Далее**.  
  
5.  На странице **Выбор подключения к базе данных** выполните одно из следующих действий:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         \-или\-  
  
    -   Нажмите кнопку **Создать подключение** для создания нового подключения к данным.  Дополнительные сведения см. в разделе [Создание подключений к базам данных SQL Server](http://msdn.microsoft.com/ru-ru/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
6.  Если база данных требует пароля, нажмите кнопку **Да, включить конфиденциальные данные в строку подключения**, а затем нажмите кнопку **Далее**.  
  
    > [!NOTE]
    >  Если появится диалоговое окно, нажмите кнопку **Да**, чтобы сохранить файл в проекте.  
  
7.  На странице **Выберите версию** выберите переключатель **Entity Framework 5.0** и нажмите кнопку **Далее**.  
  
    > [!NOTE]
    >  Чтобы использовать последнюю версию Entity Framework 6 со службами WCF, необходимо установить пакет WCF Data Services Entity Framework Provider NuGet.  См. статью [Using WCF Data Services 5.6.0 with Entity Framework 6\+ \(Использование служб WCF Data Services 5.6.0 с Entity Framework 6\+\)](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8.  На странице **Выбор объектов базы данных** разверните узел **Таблицы**, установите флажок **Customers** и нажмите кнопку **Готово**.  
  
     Будет отображена диаграмма модели сущности, и файл NorthwindModel.edmx будет добавлен в проект.  
  
 На данном этапе будет создана и протестирована служба данных.  
  
#### Создание службы данных  
  
1.  В строке меню выберите **Проект**, **Добавить новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите узел **Веб** и выберите элемент **Служба данных WCF 5.6**.  
  
3.  В текстовом поле **Имя** введите `NorthwindCustomers` и нажмите кнопку **Добавить**.  
  
     Файл NorthwindCustomers.svc появится в **редакторе кода**.  
  
4.  В **редакторе кода**, найдите первый комментарий `TODO:` и замените код следующим:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-cs[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Замените комментарии в обработчике событий `InitializeService` следующим кодом:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-cs[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  Чтобы запустить службу, в строке меню выберите **Отладка**, **Запуск без отладки**.  Откроется окно браузера, и в нем будет отображена схема XML для службы.  
  
7.  В поле **Адрес** введите `Customers` в конце URL\-адреса для файла NorthwindCustomers.svc, а затем нажмите клавишу ВВОД.  
  
     Будет отображено XML\-представление данных в таблице Customers.  
  
    > [!NOTE]
    >  В некоторых случаях обозреватель Internet Explorer может неправильно интерпретировать данные как RSS\-канал.  Необходимо убедиться, что параметр, определяющий, отображаются ли RSS\-каналы, отключен.  Дополнительные сведения см. в разделе [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
8.  Закройте окно браузера.  
  
 В ходе следующих этапов будет создано клиентское приложение Windows Forms для использования службы.  
  
## Создание клиентского приложения  
 Чтобы создать клиентское приложение, потребуется добавить второй проект, добавить к проекту ссылку на службу, настроить источник данных и создать пользовательский интерфейс, отображающий данные из службы.  
  
 Сначала проект Windows Forms добавляется к решению и устанавливается как загружаемый проект.  
  
#### Создание клиентского приложения  
  
1.  В строке меню выберите Файл, **Добавить**, **Создать проект**.  
  
2.  В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C\#**, выберите узел **Windows** и выберите элемент **Приложение Windows Forms**.  
  
3.  В поле **Имя** введите `NorthwindClient` и нажмите кнопку **ОК**.  
  
4.  В **Обозревателе решений** выберите узел проекта **NorthwindClient**.  
  
5.  В строке меню выберите **Проект**, затем **Назначить запускаемым проектом**.  
  
 На этом этапе необходимо добавить ссылку на службу [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] в веб\-проекте.  
  
#### Добавление ссылки на службу  
  
1.  В меню **Проект** выберите **Добавить ссылку на службу**.  
  
2.  В диалоговом окне **Добавить ссылку на службу** нажмите кнопку **Найти**.  
  
     В поле **Адрес** появится URL\-адрес службы NorthwindCustomers.  
  
3.  Нажмите кнопку **ОК**, чтобы добавить ссылку на службу.  
  
 На данном этапе настраивается источник данных на включение привязки данных к службе.  
  
#### Включение привязки данных к службе  
  
1.  В строке меню выберите **Вид**, **Другие окна**, **Источники данных**.  
  
2.  В окне **Источники данных** нажмите кнопку **Добавить новый источник данных**.  
  
3.  На странице **Выбор типа источника данныхмастера настройки источника данных** выберите **Объект** и нажмите кнопку **Далее**.  
  
4.  На странице **Выбор объектов данных** последовательно разверните узлы **NorthwindClient** и **NorthwindClient.ServiceReference1**.  
  
5.  Установите флажок **Customer** и нажмите кнопку **Готово**.  
  
 На данном этапе создается пользовательский интерфейс, который будет отображать данные из службы.  
  
#### Создание пользовательского интерфейса  
  
1.  В окне **Источники данных** откройте контекстное меню для узла **Customers** и выберите команду **Копировать**.  
  
2.  В конструкторе форм в файле **Form1.vb** или **Form1.cs** откройте контекстное меню и выберите команду **Вставить**.  
  
     На форму добавится элемент управления <xref:System.Windows.Forms.DataGridView>, компонент <xref:System.Windows.Forms.BindingSource> и компонент <xref:System.Windows.Forms.BindingNavigator>.  
  
3.  Выберите элемент управления **CustomersDataGridView** и в окне **Свойства** установите свойство **Закрепить** в **Заполнение**.  
  
4.  В **Обозревателе решений** откройте контекстное меню для узла **Form1** и выберите **Просмотр кода**, открыв таким образом редактор кода, а затем добавьте следующие операторы Imports или Using с начала файла:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```c#  
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
  
    ```c#  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  В **Обозревателе решений** откройте контекстное меню файла NorthwindCustomers.svc и выберите команду **Просмотреть в браузере**.  Откроется Internet Explorer, и в нем будет отображена схема XML для службы.  
  
7.  Скопируйте URL\-адрес из адресной строки обозревателя Internet Explorer.  
  
8.  В коде, добавленном на этапе 4, выберите код `http://localhost:53161/NorthwindCustomers.svc/` и замените его только что скопированным URL\-адресом.  
  
9. Чтобы запустить приложение, в строке меню выберите **Отладка**, **Начать отладку**.  Будут отображены сведения о клиенте.  
  
 Теперь в наличии имеется рабочее приложение, которое будет отображать список клиентов из службы NorthwindCustomers.  При необходимости в отображении дополнительных данных посредством службы, свойство [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] можно изменить, чтобы включить дополнительные таблицы из базы данных Northwind.  
  
 Следующим необязательным этапом является изучение фильтрации данных, возвращаемых службой.  
  
## Добавление возможностей фильтрации  
 На данном этапе будет выполнена настройка приложения на фильтрацию данных по городу клиента.  
  
#### Добавление фильтрации по городу  
  
1.  В **Обозревателе решений** откройте контекстное меню узла **Form1.vb** or **Form1.cs** и выберите команду **Открыть**.  
  
2.  Добавьте в форму элементы управления <xref:System.Windows.Forms.TextBox> и <xref:System.Windows.Forms.Button> с **панели элементов**.  
  
3.  Откройте контекстное меню элемента управления <xref:System.Windows.Forms.Button> и выберите команду **Перейти к коду**, а затем добавьте в обработчик событий `Button1_Click` следующий код:  
  
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
  
    ```c#  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  В коде выше замените `http://localhost:53161/NorthwindCustomers.svc` URL\-адресом из обработчика событий `Form1_Load`.  
  
5.  Чтобы запустить приложение, в строке меню выберите **Отладка**, **Начать отладку**.  
  
6.  В текстовом поле введите London и нажмите кнопку.  Будут отображены только клиенты из Лондона.  
  
## См. также  
 [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)