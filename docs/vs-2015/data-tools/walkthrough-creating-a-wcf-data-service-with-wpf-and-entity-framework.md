---
title: 'Пошаговое руководство: Создание службы данных WCF с помощью WPF и Entity Framework | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d115c7ea7b2739f49492fb28fe855e2638d972c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889598"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Пошаговое руководство: Создание службы данных WCF с помощью WPF и Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В этом пошаговом руководстве демонстрируется создание простого [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , размещенного в [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] веб-приложения и последующий доступ к ней из приложения Windows Forms.  
  
 В этом пошаговом руководстве:  
  
-   Создайте веб-приложение, размещаемое в [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Будет создана [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], представляющая таблицу Customers в базе данных Northwind.  
  
-   Создайте таблицу [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Создайте клиентское приложение и добавьте ссылку на [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Будет включена привязка данных к службе и создан пользовательский интерфейс.  
  
-   При необходимости в приложение будут добавлены возможности фильтрации.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Наличие учебной базы данных Northwind.  
  
     Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла [Центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=98088). Инструкции см. в разделе [Загрузка примеров баз данных](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Создание службы  
 Чтобы создать службу [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], необходимо добавить веб-проект, создать [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] и службу из модели.  
  
 Сначала добавляется веб-проект для размещения службы.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Создание веб-проекта  
  
1. В строке меню выберите **файл**, **New**, **проекта**.  
  
2. В **новый проект** диалоговое окно последовательно раскройте элементы **Visual Basic** или **Visual C#** и **Web** узлов, а затем выберите **ASP. Веб-приложения NET** шаблона.  
  
3. В **имя** текста введите **NorthwindWeb**, а затем выберите **ОК** кнопки.  
  
4. В **новый проект ASP.NET** отображаемое в диалоговом окне **выберите шаблон** выберите **пустой**, а затем выберите **ОК** кнопки.  
  
   На данном этапе будет создана [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], представляющая таблицу Customers в базе данных Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Создание модели EDM  
  
1. В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
2. В **Добавление нового элемента** диалоговое окно, выберите **данных** узел и нажмите кнопку **ADO.NET Entity Data Model** элемента.  
  
3. В **имя** текста введите `NorthwindModel`, а затем выберите **добавить** кнопки.  
  
    Появится мастер модели EDM.  
  
4. В мастере модели EDM на **Выбор содержимого модели** выберите **конструктор EF из базы данных** элемента, а затем выберите **Далее** кнопки.  
  
5. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:  
  
   -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
        - или -  
  
   -   Выберите **новое подключение** кнопку, чтобы настроить новое подключение данных. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
6. Если базе данных требуется пароль, выберите **Да, включить конфиденциальные данные в строке подключения** переключатель, а затем выберите **Далее** кнопки.  
  
   > [!NOTE]
   >  Если отображается диалоговое окно, выберите **Да** для сохранения файла в проект.  
  
7. На **Выбор версии** выберите **Entity Framework 5.0** переключатель, а затем выберите **Далее** кнопки.  
  
   > [!NOTE]
   >  Чтобы использовать последнюю версию Entity Framework 6 со службами WCF, необходимо установить пакет WCF Data Services Entity Framework Provider NuGet. См. в разделе [использование WCF Data Services 5.6.0 с Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. На **Choose Your Database Objects** странице, разверните узел **таблиц** выберите **клиентов** флажок, а затем выберите **Готово** кнопка.  
  
    Будет отображена диаграмма модели сущности, и файл NorthwindModel.edmx будет добавлен в проект.  
  
   На данном этапе будет создана и протестирована служба данных.  
  
#### <a name="to-create-the-data-service"></a>Создание службы данных  
  
1. В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
2. В **Добавление нового элемента** диалоговое окно, выберите **Web** узел и нажмите кнопку **служба данных WCF 5.6** элемента.  
  
3. В **имя** текста введите `NorthwindCustomers`, а затем выберите **добавить** кнопки.  
  
    Файл NorthwindCustomers.svc появится в **редактор кода**.  
  
4. В **редактор кода**, найдите первый `TODO:` комментарий и замените код следующим:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Замените комментарии в обработчике событий `InitializeService` следующим кодом:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. В строке меню выберите **Отладка**, **Запуск без отладки** для запуска службы. Откроется окно браузера, и в нем будет отображена схема XML для службы.  
  
7. В **адрес** введите `Customers` в конце URL-адрес для файла NorthwindCustomers.svc, а затем выберите **ввод** ключ.  
  
    Будет отображено XML-представление данных в таблице Customers.  
  
   > [!NOTE]
   >  В некоторых случаях обозреватель Internet Explorer может неправильно интерпретировать данные как RSS-канал. Необходимо убедиться, что параметр, определяющий, отображаются ли RSS-каналы, отключен. Дополнительные сведения см. в разделе [Устранение неполадок ссылок на службы](../data-tools/troubleshooting-service-references.md).  
  
8. Закройте окно браузера.  
  
   В ходе следующих этапов будет создано клиентское приложение Windows Forms для использования службы.  
  
## <a name="creating-the-client-application"></a>Создание клиентского приложения  
 Чтобы создать клиентское приложение, потребуется добавить второй проект, добавить к проекту ссылку на службу, настроить источник данных и создать пользовательский интерфейс, отображающий данные из службы.  
  
 Сначала проект Windows Forms добавляется к решению и устанавливается как загружаемый проект.  
  
#### <a name="to-create-the-client-application"></a>Создание клиентского приложения  
  
1. В строке меню выберите файл, **добавить**, **новый проект**.  
  
2. В **новый проект** диалоговое окно последовательно раскройте элементы **Visual Basic** или **Visual C#** узел и выберите **Windows** узел, а затем выберите  **Windows Forms Application**.  
  
3. В текстовом поле **Имя** введите `NorthwindClient` и нажмите кнопку **ОК**.  
  
4. В **обозревателе решений**, выберите **NorthwindClient** узел проекта.  
  
5. В строке меню выберите **проекта**, **Назначить запускаемым проектом**.  
  
   На этом этапе необходимо добавить ссылку на службу [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] в веб-проекте.  
  
#### <a name="to-add-a-service-reference"></a>Добавление ссылки на службу  
  
1. В строке меню выберите **проекта**, **Add Service Reference**.  
  
2. В **Add Service Reference** диалоговое окно, выберите **Discover** кнопки.  
  
    URL-адрес службы NorthwindCustomers отображается в **адрес** поля.  
  
3. Выберите **ОК** кнопку, чтобы добавить ссылку на службу.  
  
   На данном этапе настраивается источник данных на включение привязки данных к службе.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Включение привязки данных к службе  
  
1. В строке меню выберите **представление**, **Other Windows**, **источников данных**.  
  
2. В **источников данных** окно, выберите **добавить новый источник данных** кнопки.  
  
3. На **Выбор типа источника данных** странице **мастер настройки источника данных**, выберите **объект**и нажмите кнопку **Далее** кнопки .  
  
4. На **Выбор объектов данных** странице, разверните узел **NorthwindClient** узел, а затем разверните **NorthwindClient.ServiceReference1** узла.  
  
5. Выберите **клиента** , а затем нажать **Готово** кнопки.  
  
   На данном этапе создается пользовательский интерфейс, который будет отображать данные из службы.  
  
#### <a name="to-create-the-user-interface"></a>Создание пользовательского интерфейса  
  
1. В **источников данных** окно, откройте контекстное меню для **клиентов** узел и выберите **копирования**.  
  
2. В **Form1.vb** или **Form1.cs** конструкторе форм, откройте контекстное меню и выберите **вставить**.  
  
    На форму добавится элемент управления <xref:System.Windows.Forms.DataGridView>, компонент <xref:System.Windows.Forms.BindingSource> и компонент <xref:System.Windows.Forms.BindingNavigator>.  
  
3. Выберите **CustomersDataGridView** элемента управления, а затем в **свойства** окно набора **закрепления** свойства **заполнения**.  
  
4. В **обозревателе решений**, откройте контекстное меню для **Form1** узел и выберите **Просмотр кода** чтобы открыть редактор кода и добавьте следующие операторы Imports или Using в начало файла:  
  
   ```vb  
   Imports NorthwindClient.ServiceReference1  
   ```  
  
   ```csharp  
   using NorthwindClient.ServiceReference1;  
   ```  
  
5. Добавьте следующий код в обработчик событий `Form1_Load` .  
  
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
  
6. В **обозревателе решений**, откройте контекстное меню файла NorthwindCustomers.svc и выберите **просмотреть в браузере**. Откроется Internet Explorer, и в нем будет отображена схема XML для службы.  
  
7. Скопируйте URL-адрес из адресной строки обозревателя Internet Explorer.  
  
8. В коде, добавленном на этапе 4, выберите код `http://localhost:53161/NorthwindCustomers.svc/` и замените его только что скопированным URL-адресом.  
  
9. В строке меню выберите **Отладка**, **начать отладку** для запуска приложения. Будут отображены сведения о клиенте.  
  
   Теперь в наличии имеется рабочее приложение, которое будет отображать список клиентов из службы NorthwindCustomers. При необходимости в отображении дополнительных данных посредством службы, свойство [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] можно изменить, чтобы включить дополнительные таблицы из базы данных Northwind.  
  
   Следующим необязательным этапом является изучение фильтрации данных, возвращаемых службой.  
  
## <a name="adding-filtering-capabilities"></a>Добавление возможностей фильтрации  
 На данном этапе будет выполнена настройка приложения на фильтрацию данных по городу клиента.  
  
#### <a name="to-add-filtering-by-city"></a>Добавление фильтрации по городу  
  
1.  В **обозревателе решений**, откройте контекстное меню для **Form1.vb** или **Form1.cs** узел и выберите **откройте**.  
  
2.  Добавить <xref:System.Windows.Forms.TextBox> управления и <xref:System.Windows.Forms.Button> управления из **элементов** в форму.  
  
3.  Откройте контекстное меню для <xref:System.Windows.Forms.Button> управлять и **Просмотр кода**, а затем добавьте следующий код в `Button1_Click` обработчик событий:  
  
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
  
5.  В строке меню выберите **Отладка**, **начать отладку** для запуска приложения.  
  
6.  В текстовом поле введите **Лондон**и нажмите кнопку "". Будут отображены только клиенты из Лондона.  
  
## <a name="see-also"></a>См. также  
 [Службы Windows Communication Foundation и WCF Data Services в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Практическое руководство. Добавление, обновление или удаление ссылки на службу данных WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)

