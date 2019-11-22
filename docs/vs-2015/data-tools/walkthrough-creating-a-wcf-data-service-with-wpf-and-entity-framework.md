---
title: 'Walkthrough: Creating a WCF Data Service with WPF and Entity Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5abbb647f93c991d2de626a84e82f47e03f6f71e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299623"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Пошаговое руководство. Создание службы данных WCF с помощью WPF и Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

This walkthrough demonstrates how to create a simple [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] that is hosted in an [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web application and then access it from a Windows Forms application.

 В этом пошаговом руководстве:

- Создайте веб-приложение, размещаемое в [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Будет создана [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], представляющая таблицу Customers в базе данных Northwind.

- Создайте таблицу [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Создайте клиентское приложение и добавьте ссылку на [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Будет включена привязка данных к службе и создан пользовательский интерфейс.

- При необходимости в приложение будут добавлены возможности фильтрации.

## <a name="prerequisites"></a>Необходимые компоненты
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- Наличие учебной базы данных Northwind.

     Если база данных не установлена на компьютере разработчика, загрузите ее с веб-узла [Центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?LinkID=98088). For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).

## <a name="creating-the-service"></a>Создание службы
 Чтобы создать службу [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], необходимо добавить веб-проект, создать [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] и службу из модели.

 Сначала добавляется веб-проект для размещения службы.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-the-web-project"></a>Создание веб-проекта

1. On the menu bar, choose **File**, **New**,  **Project**.

2. В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C#** и выберите пункт **Веб**, а затем выберите шаблон **Веб-приложение ASP.NET**.

3. В текстовом поле **Имя** введите **NorthwindWeb** и нажмите кнопку **ОК**.

4. В диалоговом окне **Новый проект ASP.NET** в списке **Выбор шаблона** выберите **Пустой**, а затем нажмите кнопку **ОК**.

   На данном этапе будет создана [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], представляющая таблицу Customers в базе данных Northwind.

#### <a name="to-create-the-entity-data-model"></a>Создание модели EDM

1. On the menu bar, choose **Project**, **Add New Item**.

2. В диалоговом окне **Добавление нового элемента** выберите узел **Данные** и выберите элемент **Модель EDM ADO.NET**.

3. In the **Name** text box, enter `NorthwindModel`, and then choose the **Add** button.

    Появится мастер модели EDM.

4. В мастере моделей EDM на странице **Выбор модели содержимого** выберите элемент **Конструктор EF из базы данных** и нажмите кнопку **Далее**.

5. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

   - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

        \- или -

   - Нажмите кнопку **Создать подключение** для создания нового подключения к данным. For more information, see [Add new connections](../data-tools/add-new-connections.md).

6. Если база данных требует пароль, нажмите кнопку **Да, включить конфиденциальные данные в строку подключения**, а затем нажмите кнопку **Далее**.

   > [!NOTE]
   > Если появится диалоговое окно, выберите **Да**, чтобы сохранить файл в проекте.

7. На странице **Выберите версию** выберите переключатель **Entity Framework 5.0** и нажмите кнопку **Далее**.

   > [!NOTE]
   > Чтобы использовать последнюю версию Entity Framework 6 со службами WCF, необходимо установить пакет WCF Data Services Entity Framework Provider NuGet. See [Using WCF Data Services 5.6.0 with Entity Framework 6+](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. На странице **Выбор объектов базы данных** разверните узел **Таблицы**, установите флажок **Customers** и нажмите кнопку **Готово**.

    Будет отображена диаграмма модели сущности, и файл NorthwindModel.edmx будет добавлен в проект.

   На данном этапе будет создана и протестирована служба данных.

#### <a name="to-create-the-data-service"></a>Создание службы данных

1. On the menu bar, choose **Project**, **Add New Item**.

2. В диалоговом окне **Добавление нового элемента** выберите узел **Веб** и элемент **Служба данных WCF 5.6**.

3. In the **Name** text box, enter `NorthwindCustomers`, and then choose the **Add** button.

    The NorthwindCustomers.svc file appears in the **Code Editor**.

4. В **редакторе кода** найдите первый комментарий `TODO:` и замените код следующим:

    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]

5. Замените комментарии в обработчике событий `InitializeService` следующим кодом:

    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]

6. On the menu bar, choose **Debug**, **Start Without Debugging** to run the service. Откроется окно браузера, и в нем будет отображена схема XML для службы.

7. In the **Address** bar, enter `Customers` at the end of the URL for NorthwindCustomers.svc, and then choose the **ENTER** key.

    Будет отображено XML-представление данных в таблице Customers.

   > [!NOTE]
   > В некоторых случаях обозреватель Internet Explorer может неправильно интерпретировать данные как RSS-канал. Необходимо убедиться, что параметр, определяющий, отображаются ли RSS-каналы, отключен. For more information, see [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).

8. Закройте окно браузера.

   В ходе следующих этапов будет создано клиентское приложение Windows Forms для использования службы.

## <a name="creating-the-client-application"></a>Создание клиентского приложения
 Чтобы создать клиентское приложение, потребуется добавить второй проект, добавить к проекту ссылку на службу, настроить источник данных и создать пользовательский интерфейс, отображающий данные из службы.

 Сначала проект Windows Forms добавляется к решению и устанавливается как загружаемый проект.

#### <a name="to-create-the-client-application"></a>Создание клиентского приложения

1. On the menu bar, choose File, **Add**, **New Project**.

2. In the **New Project** dialog box, expand the **Visual Basic** or **Visual C#** node and choose the **Windows** node, and then choose **Windows Forms Application**.

3. В текстовом поле **Имя** введите `NorthwindClient` и нажмите кнопку **ОК**.

4. В **обозревателе решений** выберите узел проекта **NorthwindClient**.

5. В строке меню выберите **Проект**, затем **Назначить запускаемым проектом**.

   На этом этапе необходимо добавить ссылку на службу [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] в веб-проекте.

#### <a name="to-add-a-service-reference"></a>Добавление ссылки на службу

1. On the menu bar, choose **Project**, **Add Service Reference**.

2. В диалоговом окне **Добавление ссылки на службу** нажмите кнопку **Найти**.

    В поле **Адрес** появится URL-адрес службы NorthwindCustomers.

3. Нажмите кнопку **ОК**, чтобы добавить ссылку на службу.

   На данном этапе настраивается источник данных на включение привязки данных к службе.

#### <a name="to-enable-data-binding-to-the-service"></a>Включение привязки данных к службе

1. On the menu bar, choose **View**, **Other Windows**, **Data Sources**.

2. В окне **Источники данных** нажмите кнопку **Добавить новый источник данных**.

3. На странице **Выбор типа источника данных** **мастера настройки источника данных** выберите **Объект** и нажмите кнопку **Далее**.

4. На странице **Выбор объектов данных** последовательно разверните узлы **NorthwindClient** и **NorthwindClient.ServiceReference1**.

5. Установите флажок **Customer** и нажмите кнопку **Готово**.

   На данном этапе создается пользовательский интерфейс, который будет отображать данные из службы.

#### <a name="to-create-the-user-interface"></a>Создание пользовательского интерфейса

1. В окне **Источники данных** откройте контекстное меню для узла **Customers** и выберите команду **Копировать**.

2. В конструкторе форм в файле **Form1.vb** или **Form1.cs** откройте контекстное меню и выберите команду **Вставить**.

    На форму добавится элемент управления <xref:System.Windows.Forms.DataGridView>, компонент <xref:System.Windows.Forms.BindingSource> и компонент <xref:System.Windows.Forms.BindingNavigator>.

3. Выберите элемент управления **CustomersDataGridView** и в окне **Свойства** установите для свойства **Закрепить** значение **Заполнение**.

4. In **Solution Explorer**, open the shortcut menu for the **Form1** node and choose **View Code** to open the Code Editor, and add the following Imports or Using statement at the top of the file:

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

6. In **Solution Explorer**, open the shortcut menu for the NorthwindCustomers.svc file and choose **View in Browser**. Откроется Internet Explorer, и в нем будет отображена схема XML для службы.

7. Скопируйте URL-адрес из адресной строки обозревателя Internet Explorer.

8. В коде, добавленном на этапе 4, выберите код `http://localhost:53161/NorthwindCustomers.svc/` и замените его только что скопированным URL-адресом.

9. On the menu bar, choose **Debug**, **Start Debugging** to run the application. Будут отображены сведения о клиенте.

   Теперь в наличии имеется рабочее приложение, которое будет отображать список клиентов из службы NorthwindCustomers. При необходимости в отображении дополнительных данных посредством службы, свойство [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] можно изменить, чтобы включить дополнительные таблицы из базы данных Northwind.

   Следующим необязательным этапом является изучение фильтрации данных, возвращаемых службой.

## <a name="adding-filtering-capabilities"></a>Добавление возможностей фильтрации
 На данном этапе будет выполнена настройка приложения на фильтрацию данных по городу клиента.

#### <a name="to-add-filtering-by-city"></a>Добавление фильтрации по городу

1. В **обозревателе решений** откройте контекстное меню узла **Form1.vb** или **Form1.cs** и выберите команду **Открыть**.

2. Добавьте в форму элементы управления <xref:System.Windows.Forms.TextBox> и <xref:System.Windows.Forms.Button> с **панели элементов**.

3. Open the shortcut menu for the <xref:System.Windows.Forms.Button> control, and choose **View Code**, and then add the following code in the `Button1_Click` event handler:

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

4. В коде выше замените `http://localhost:53161/NorthwindCustomers.svc` URL-адресом из обработчика событий `Form1_Load`.

5. On the menu bar, choose **Debug**, **Start Debugging** to run the application.

6. В текстовом поле введите **London** и нажмите кнопку. Будут отображены только клиенты из Лондона.

## <a name="see-also"></a>См. также раздел
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
