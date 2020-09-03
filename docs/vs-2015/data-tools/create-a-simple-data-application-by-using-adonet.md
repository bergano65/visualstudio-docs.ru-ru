---
title: Создание простого приложения для данных с помощью ADO.NET | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b524c9d630f30edd226265ac150ef7ec4f6c60d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651075"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Создание простого приложения для работы с данными с помощью ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании приложения, которое работает с данными в базе данных, необходимо выполнить такие основные задачи, как определение строк подключения, вставка данных и выполнение хранимых процедур. В этом разделе вы узнаете, как взаимодействовать с базой данных из простого Windows Forms приложения "формы по данным" с помощью Visual C#, Visual Basic и ADO.NET.  Все технологии данных .NET, в том числе наборы данных, LINQ to SQL и Entity Framework, в конечном итоге выполняют шаги, которые очень похожи на те, которые приведены в этой статье.

 В этой статье демонстрируется простой способ быстро получить данные из базы данных. Если приложению необходимо изменить данные с помощью нетривиальных способов и обновить базу данных, следует рассмотреть возможность использования Entity Framework и привязки данных для автоматической синхронизации элементов управления пользовательского интерфейса с изменениями в базовых данных.

> [!IMPORTANT]
> С целью упрощения код не включает обработку исключений для выполнения в рабочей среде.

 **Содержание раздела**

- [Настройка образца базы данных](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)

- [Создание форм и добавление элементов управления](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)

- [Сохранение строки подключения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)

- [Получение строки подключения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)

- [Написание кода для форм](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)

- [Тестирование приложения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)

## <a name="prerequisites"></a>Предварительные требования
 Для создания приложения вам потребуются следующие компоненты.

- Выпуск Visual Studio Community.

- SQL Server Express LocalDB.

- Небольшой образец базы данных, который вы создадите, выполнив действия, описанные в разделе [Создание базы данных SQL с помощью скрипта](../data-tools/create-a-sql-database-by-using-a-script.md).

- Строка подключения для базы данных после ее настройки. Это значение можно найти, открыв **Обозреватель объектов SQL Server**, открыв контекстное меню для базы данных, выбрав пункт **свойства**, а затем прокрутите его до свойства **ConnectionString**  .

  В рамках этого раздела предполагается, что вы уже знакомы с основными функциями интегрированной среды разработки Visual Studio и можете создать приложение Windows Forms, добавить формы в проект, добавить кнопки и другие элементы управления в формы, задать свойства для этих элементов управления и создать код для простых событий. Если вы не знакомы с этими задачами, мы рекомендуем завершить [Начало работы с помощью Visual C# и Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) , прежде чем начать этот раздел.

## <a name="set-up-the-sample-database"></a><a name="BKMK_setupthesampledatabase"></a> Настройка образца базы данных
 Пример базы данных для этого пошагового руководства состоит из таблиц клиентов и заказов. Изначально таблицы не содержат данные, однако вы добавите данные при выполнении созданного приложения. База данных также имеет пять простых хранимых процедур. [Создание базы данных SQL с помощью скрипта](../data-tools/create-a-sql-database-by-using-a-script.md) содержит скрипт TRANSACT-SQL, который создает таблицы, первичные и внешние ключи, ограничения и хранимые процедуры.

## <a name="create-the-forms-and-add-controls"></a><a name="BKMK_createtheformsandaddcontrols"></a> Создание форм и добавление элементов управления

1. Создайте проект для приложения Windows Forms и назовите его SimpleDataApp.

    Visual Studio создает проект и несколько файлов, включая пустую форму Windows Forms с именем Form1.

2. Добавьте две формы Windows Forms в проект, чтобы он включал три формы, и назначьте им следующие имена:

   - Навигация

   - NewCustomer

   - FillOrCancel

3. Для каждой формы добавьте текстовые поля, кнопки и другие элементы управления, которые отображаются на рисунках ниже. Для каждого элемента управления задайте свойства, указанные в таблицах.

   > [!NOTE]
   > Элементы управления "группа" и "надпись" обеспечивают большую ясность, но не используются в коде.

   **Форма навигации**

   ![Диалоговое окно "Навигация"](../data-tools/media/simpleappnav.png "симплеаппнав")

|Элементы управления формы навигации|Свойства|
|--------------------------------------|----------------|
|Кнопка|Name = btnGoToAdd|
|Кнопка|Name = btnGoToFillOrCancel|
|Кнопка|Name = btnExit|

 **Форма NewCustomer**

 ![Добавление нового заказчика и размещение заказа](../data-tools/media/simpleappnewcust.png "симплеаппневкуст")

|Элементы управления формы NewCustomer|Свойства|
|---------------------------------------|----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|Кнопка|Name = btnCreateAccount|
|NumericUpDown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|Кнопка|Name = btnPlaceOrder|
|Кнопка|Name = btnAddAnotherAccount|
|Кнопка|Name = btnAddFinish|

 **Форма FillOrCancel**

 ![заполнение или отмена заказов](../data-tools/media/simpleappcancelfill.png "симплеаппканцелфилл")

|Элементы управления формы FillOrCancel|Свойства|
|----------------------------------------|----------------|
|TextBox|Name = txtOrderID|
|Кнопка|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Кнопка|Name = btnCancelOrder|
|Кнопка|Name = btnFillOrder|
|Кнопка|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a><a name="BKMK_storetheconnectionstring"></a> Сохранение строки подключения
 Когда приложение пытается открыть подключение к базе данных, оно должно иметь доступ к строке подключения. Чтобы не вводить строку вручную в каждой форме, сохраните строку в файле конфигурации приложения в проекте и создайте метод, возвращающий строку при вызове метода из любой формы в приложении.

 Строку подключения можно найти в **Обозреватель объектов SQL Server** , щелкнув базу данных правой кнопкой мыши, выбрав пункт **свойства**, а затем находя свойство ConnectionString. Используйте сочетание клавиш CTRL + A, чтобы выбрать строку.

1. В **Обозреватель решений**выберите узел **свойства** в проекте, а затем щелкните **Settings. Settings**.

2. В столбце **имя** введите `connString` .

3. В списке **тип** выберите **(строка подключения)**.

4. В списке **область** выберите **приложение**.

5. В столбце **значение** введите строку подключения (без кавычек), а затем сохраните изменения.

> [!NOTE]
> В реальных приложениях строку подключения следует хранить безопасно, как описано в разделе [строки подключения и файлы конфигурации](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).

## <a name="retrieve-the-connection-string"></a><a name="BKMK_retrievetheconnectionstring"></a> Получение строки подключения

1. В строке меню выберите **проект**  >  **Добавить ссылку**, а затем добавьте ссылку на System.Configuration.dll.

2. В строке меню выберите **проект**  >  **Добавить класс** , чтобы добавить в проект файл класса, а затем назовите файл `Utility` .

     Visual Studio создаст файл и отобразит его в **Обозреватель решений**.

3. В файле Utility замените код-заполнитель следующим кодом. Обратите внимание на нумерованные комментарии (с префиксом Util-), которые указывают разделы кода. В таблице под примером кода описаны ключевые моменты.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    //Util-1 More namespaces.
    using System.Configuration;

    namespace SimpleDataApp
    {
        internal class Utility
        {

            //Get the connection string from App config file.
            internal static string GetConnectionString()
            {
                //Util-2 Assume failure.
                string returnValue = null;

                //Util-3 Look for the name in the connectionStrings section.
                ConnectionStringSettings settings =
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];

                //If found, return the connection string.
                if (settings != null)
                    returnValue = settings.ConnectionString;

                return returnValue;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.Collections.Generic
    Imports System.Linq
    Imports System.Text
    Imports System.Threading.Tasks
    ' Util-1 More namespaces.
    Imports System.Configuration

    Namespace SimpleDataApp
        Friend Class Utility

            ' Get connection string from App config file.
            Friend Shared Function GetConnectionString() As String

                ' Util-2 Assume failure.
                Dim returnValue As String = Nothing

                ' Util-3 Look for the name in the connectionStrings section.
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")

                ' If found, return the connection string.
                If settings IsNot Nothing Then
                    returnValue = settings.ConnectionString
                End If

                Return returnValue
            End Function
        End Class
    End Namespace
    ```

    |Комментировать|Описание|
    |-------------|-----------------|
    |Util-1|Добавление пространства имен `System.Configuration`|
    |Util-2|Определение переменной `returnValue` и ее инициализация значением `null` (C#) или `Nothing` (Visual Basic).|
    |Util-3|Несмотря на то `connString` , что в окне " **свойства** " в качестве имени строки подключения необходимо указать `"SimpleDataApp.Properties.Settings.connString"` (C#) или `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) в коде.|

## <a name="write-the-code-for-the-forms"></a><a name="BKMK_writethecodefortheforms"></a> Написание кода для форм
 Этот раздел содержит краткий обзор функций каждой формы и примеры кода для создания форм. Нумерованные комментарии указывают разделы кода.

### <a name="navigation-form"></a>Форма навигации
 Форма навигации открывается при запуске приложения. Кнопка **Добавить учетную запись** открывает форму NewCustomer. Кнопка **Выполнение или отмена заказов** открывает форму FillOrCancel. Кнопка **Выход** закрывает приложение.

#### <a name="make-the-navigation-form-the-startup-form"></a>Преобразование формы навигации в начальную форму
 Если вы используете C#, в **Обозреватель решений**откройте Program.cs, а затем измените `Application.Run` строку следующим образом: `Application.Run(new Navigation());`

 Если вы используете Visual Basic, в **Обозреватель решений**откройте окно **свойства** , перейдите на вкладку **приложение** и выберите **симпледатаапп. Navigation** в списке **начальных форм** .

#### <a name="create-event-handlers"></a>Создание обработчиков событий
 Дважды щелкните три кнопки в форме, чтобы создать пустые методы обработчика событий.

#### <a name="create-code-for-navigation"></a>Создание кода для навигации
 В форме навигации замените существующий код следующим кодом.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace SimpleDataApp
{
    public partial class Navigation : Form
    {
        public Navigation()
        {
            InitializeComponent();
        }

        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        private void btnGoToAdd_Click(object sender, EventArgs e)
        {
            Form frm = new NewCustomer();
            frm.Show();
        }

        //Open the FillorCancel form as a dialog box.
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)
        {
            Form frm = new FillOrCancel();
            frm.ShowDialog();
        }

        //Close the application, not just the Navigation form.
        private void btnExit_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms

Namespace SimpleDataApp
    Partial Public Class Navigation
        Inherits Form
        Public Sub New()
            InitializeComponent()
        End Sub

        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click
            Dim frm As Form = New NewCustomer()
            frm.Show()
        End Sub

        ' Open the FillorCancel form as a dialog box.
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click
            Dim frm As Form = New FillOrCancel()
            frm.ShowDialog()
        End Sub

        ' Close the application, not just the Navigation form.
        Private Sub btnExit_Click() Handles btnExit.Click
            Me.Close()
        End Sub
    End Class
End Namespace

```

### <a name="newcustomer-form"></a>Форма NewCustomer
 При вводе имени клиента и нажатии кнопки **создать учетную запись** форма newCustomer создает учетную запись клиента, а SQL Server ВОЗВРАЩАЕТ значение идентификатора в качестве нового номера счета. Затем можно разместить заказ для новой учетной записи, указав сумму и дату заказа, а затем нажав кнопку **поместить порядок** .

#### <a name="create-event-handlers"></a>Создание обработчиков событий
 Создайте пустой обработчик события нажатия для каждой кнопки в форме.

#### <a name="create-code-for-newcustomer"></a>Создание кода для NewCustomer
 Добавьте следующий код в форму NewCustomer. Пошагово выполните каждый блок кода, используя нумерованные комментарии и таблицу под примером кода.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//NC-1 More namespaces.
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class NewCustomer : Form
    {
        //NC-2 Storage for IDENTITY values returned from database.
        private int parsedCustomerID;
        private int orderID;

        //NC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public NewCustomer()
        {
            InitializeComponent();
        }

        //NC-4 Create account.
        private void btnCreateAccount_Click(object sender, EventArgs e)
        {
            //NC-5 Set up and run stored procedure only if Customer Name is present.
            if (isCustomerName())
            {

                //NC-6 Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-7 Create a SqlCommand, and identify it as a stored procedure.
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;

                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;

                //NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;

                //NC-10 try-catch-finally
                try
                {
                    //NC-11 Open the connection.
                    conn.Open();

                    //NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery();

                    //NC-13 Customer ID is an IDENTITY value from the database.
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);

                }
                catch
                {
                    //NC-14 A simple catch.

                    MessageBox.Show("Customer ID was not returned. Account could not be created.");
                }
                finally
                {
                    //NC-15 Close the connection.
                    conn.Close();
                }
            }
        }

        //NC-16 Verify that Customer Name is present.
        private bool isCustomerName()
        {
            if (txtCustomerName.Text == "")
            {
                MessageBox.Show("Please enter a name.");
                return false;
            }
            else
            {
                return true;
            }
        }

        //NC-17 Place order.
        private void btnPlaceOrder_Click(object sender, EventArgs e)
        {
            //NC-18 Set up and run stored procedure only if required input is present.
            if (isPlaceOrderReady())
            {
                // Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-19 Create SqlCommand and identify it as a stored procedure.
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);
                cmdNewOrder.CommandType = CommandType.StoredProcedure;

                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;

                //NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;

                //NC-22 @Amount.
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;

                //NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));
                cmdNewOrder.Parameters["@Status"].Value = "O";

                //NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;

                //try-catch-finally
                try
                {
                    //Open connection.
                    conn.Open();

                    //Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery();

                    //NC-25 Display the order number.
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("Order could not be placed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //NC-26 Verify that order data is ready.
        private bool isPlaceOrderReady()
        {
            // Verify that CustomerID is present.
            if (txtCustomerID.Text == "")
            {
                MessageBox.Show("Please create customer account before placing order.");
                return false;
            }

            // Verify that Amount isn't 0.
            else if ((numOrderAmount.Value < 1))
            {
                MessageBox.Show("Please specify an order amount.");
                return false;
            }
            else
            {
                // Order can be submitted.
                return true;
            }
        }

        //NC-27 Reset the form for another new account.
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)
        {
            this.ClearForm();
        }

        //NC-28 Clear values from controls.
        private void ClearForm()
        {
            txtCustomerName.Clear();
            txtCustomerID.Clear();
            dtpOrderDate.Value = DateTime.Now;
            numOrderAmount.Value = 0;
            this.parsedCustomerID = 0;
        }

        //NC-29 Close the form.
        private void btnAddFinish_Click(object sender, EventArgs e)
        {
            this.Close();
        }

    }
}

```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' NC-1 More namespaces.
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class NewCustomer
        Inherits Form

        ' NC-2 Storage for IDENTITY values returned from database.
        Private parsedCustomerID As Integer
        Private orderID As Integer

        ' NC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' NC-4 Create account.
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click

            ' NC-5 Set up and run stored procedure only if Customer Name is present.
            If isCustomerName() Then

                ' NC-6 Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)
                cmdNewCustomer.CommandType = CommandType.StoredProcedure

                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text

                ' NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output

                ' NC-10 try-catch-finally
                Try
                    ' NC-11 Open the connection.
                    conn.Open()

                    ' NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery()

                    ' NC-13 Customer ID is an IDENTITY value from the database.
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)

                Catch
                    ' NC-14 A simple catch.
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")
                Finally
                    ' NC-15 Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-16 Verify that Customer Name is present.
        Private Function isCustomerName() As Boolean
            If txtCustomerName.Text = "" Then
                MessageBox.Show("Please enter a name.")
                Return False
            Else
                Return True
            End If
        End Function

        ' NC-17 Place order.
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click

            ' NC-18 Set up and run stored procedure only if necessary input is present.
            If isPlaceOrderReady() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-19 Create SqlCommand and identify it as a stored procedure.
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)
                cmdNewOrder.CommandType = CommandType.StoredProcedure

                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID

                ' NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value

                ' NC-22 @Amount.
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value

                ' NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))
                cmdNewOrder.Parameters("@Status").Value = "O"

                ' NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue

                ' try-catch-finally
                Try
                    ' Open connection.
                    conn.Open()

                    ' Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery()

                    ' NC-25 Display the order number.
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")

                Catch
                    ' A simple catch.
                    MessageBox.Show("Order could  not be placed.")

                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-26 Verify that order data is ready.
        Private Function isPlaceOrderReady() As Boolean

            ' Verify that CustomerID is present.
            If txtCustomerID.Text = "" Then
                MessageBox.Show("Please create customer account before placing order.")
                Return False

                ' Verify that Amount isn't 0.
            ElseIf (numOrderAmount.Value < 1) Then

                MessageBox.Show("Please specify an order amount.")
                Return False
            Else
                ' Order can be submitted.
                Return True
            End If
        End Function

        ' NC-27 Reset the form for another new account.
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click
            Me.ClearForm()
        End Sub

        ' NC-28 Clear values from controls.
        Private Sub ClearForm()
            txtCustomerName.Clear()
            txtCustomerID.Clear()
            dtpOrderDate.Value = DateTime.Now
            numOrderAmount.Value = 0
            Me.parsedCustomerID = 0
        End Sub

        ' NC-29 Close the form.
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click
            Me.Close()
        End Sub

    End Class
End Namespace
```

|Комментировать|Описание|
|-------------|-----------------|
|NC-1|Добавьте `System.Data.SqlClient` и `System.Configuration` в список пространств имен.|
|NC-2|Объявление переменных `parsedCustomerID` и `orderID`, которые будут использоваться позже.|
|NC-3|Вызов метода `GetConnectionString` для получения строки подключения из файла конфигурации приложения и сохранение значения в строковую переменную `connstr`.|
|NC-4|Добавление кода в обработчик события нажатия кнопки `btnCreateAccount`.|
|NC-5|Создание оболочки для кода события нажатия кнопки с помощью вызова `isCustomerName`, чтобы процедура `uspNewCustomer` выполнялась только в том случае, если указано имя клиента.|
|NC-6|Создание объекта `SqlConnection` (`conn`) и передача в строке подключения в `connstr`.|
|NC-7|Создание объекта `SqlCommand`, `cmdNewCustomer`.<br /><br /> — Укажите в `Sales.uspNewCustomer` качестве выполняемой хранимой процедуры.<br />— Используйте `CommandType` свойство, чтобы указать, что команда является хранимой процедурой.|
|NC-8|Добавление входного параметра `@CustomerName` из хранимой процедуры.<br /><br /> — Добавьте параметр в `Parameters` коллекцию.<br />— Используйте `SqlDbType` перечисление, чтобы указать тип параметра в виде nvarchar (40).<br />— Укажите в `txtCustomerName.Text` качестве источника.|
|NC-9|Добавление выходного параметра из хранимой процедуры.<br /><br /> — Добавьте параметр в `Parameters` коллекцию.<br />— Используйте `ParameterDirection.Output` для задания параметра в качестве выходных данных.|
|NC-10|Добавьте блок try-catch-finally, чтобы открыть подключение, выполните хранимую процедуру, обработайте исключения, а затем закройте подключение.|
|NC-11|Открытие подключения (`conn`), созданного в шаге NC-6.|
|NC-12|Для `ExecuteNonQuery`  `cmdNewCustomer` запуска `Sales.uspNewCustomer` хранимой процедуры используйте метод. Эта хранимая процедура выполняет `INSERT` инструкцию, а не запрос.|
|NC-13|Значение `@CustomerID` возвращается как значение идентификатора из базы данных. Так как это целое число, необходимо преобразовать его в строку, чтобы отобразить ее в текстовом поле **идентификатор клиента** .<br /><br /> — Вы объявили `parsedCustomerID` в NC-2.<br />— Сохраните `@CustomerID` значение в `parsedCustomerID` для последующего использования.<br />— Преобразуйте возвращенный идентификатор клиента в строку и вставьте его в `txtCustomerID.Text` .|
|NC-14|Для этого образца добавьте простое предложение catch (не производственно-Quality).|
|NC-15|Всегда закрывайте подключение, после того как закончите его использование, чтобы его можно было вернуть в пул подключений. См. раздел [SQL Server подключения к пулам (ADO.NET)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|
|NC-16|Определите метод для проверки наличия имени клиента.<br /><br /> — Если текстовое поле пусто, отобразится сообщение и возвращается `false` , так как для создания учетной записи требуется имя.<br />— Если текстовое поле не пустое, возвращается значение `true` .|
|NC-17|Добавление кода в обработчик события нажатия кнопки `btnPlaceOrder`.|
|NC-18|Создание оболочки для кода события `btnPlaceOrder_Click` путем вызова `isPlaceOrderReady`, чтобы процедура `uspPlaceNewOrder` не выполнялась, если отсутствуют необходимые входные данные.|
|С NC-19 по NC-25|Эти фрагменты кода напоминают код, добавленный для обработчика событий `btnCreateAccount_Click`.<br /><br /> -NC-19. Создание объекта `SqlCommand`, `cmdNewOrder` и задание `Sales.uspPlaceOrder` в качестве хранимой процедуры.<br />-NC-20 – NC-23 — входные параметры для хранимой процедуры.<br />-NC-24. `@RC` будет содержать возвращаемое значение, которое представляет идентификатор созданного заказа из базы данных. Направление этого параметра указывается как `ReturnValue`.<br />-NC-25. Сохранение значения идентификатора заказа в переменной `orderID`, объявленной в шаге NC-2, и отображение значения в окне сообщения.|
|NC-26|Определение метода для проверки того, что идентификатор клиента существует и в поле `numOrderAmount` указано количество.|
|NC-27|Вызов метода `ClearForm` в обработчике события нажатия кнопки `btnAddAnotherAccount`.|
|NC-28|Создание метода `ClearForm` для сброса значений в форме, если требуется добавить другого клиента.|
|NC-29|Закрытие формы NewCustomer и возврат фокуса в форму навигации.|

### <a name="fillorcancel-form"></a>Форма FillOrCancel
 Форма Филлорканцел запускает запрос для возврата заказа при вводе идентификатора заказа и нажатии кнопки **найти заказ** . Возвращенная строка отображается в сетке данных только для чтения. Можно пометить заказ как отмененный (X), если нажать кнопку **отменить заказ** или пометить заказ как заполненный (F), если нажать кнопку **заполнить заказ** . Если нажать кнопку **найти порядок** еще раз, появится обновленная строка.

#### <a name="create-event-handlers"></a>Создание обработчиков событий
 Создайте пустые обработчики события нажатия кнопки для четырех кнопок в форме.

#### <a name="create-code-for-fillorcancel"></a>Создание кода для FillOrCancel
 Добавьте следующий код в форму FillOrCancel. Пошагово выполните блоки кода, используя нумерованные комментарии и таблицу под примером кода.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//FC-1 More namespaces.
using System.Text.RegularExpressions;
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class FillOrCancel : Form
    {
        //FC-2 Storage for OrderID.
        private int parsedOrderID;

        //FC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public FillOrCancel()
        {
            InitializeComponent();
        }

        //FC-4 Find an order.
        private void btnFindByOrderID_Click(object sender, EventArgs e)
        {
            //FC-5 Prepare the connection and the command.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Define a query string that has a parameter for orderID.
                string sql = "select * from Sales.Orders where orderID = @orderID";

                //Create a SqlCommand object.
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);

                //Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;

                //try-catch-finally
                try
                {
                    //FC-6 Run the command and display the results.
                    //Open the connection.
                    conn.Open();

                    //Run the command by using SqlDataReader.
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();

                    //Create a data table to hold the retrieved data.
                    DataTable dataTable = new DataTable();

                    //Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr);

                    //Display the data from the data table in the data grid view.
                    this.dgvCustomerOrders.DataSource = dataTable;

                    //Close the SqlDataReader.
                    rdr.Close();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-7 Cancel an order.
        private void btnCancelOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                // Create command and identify it as a stored procedure.
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;

                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;

                // try-catch-finally
                try
                {
                    // Open the connection.
                    conn.Open();

                    // Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery();
                }
                // A simple catch.
                catch
                {
                    MessageBox.Show("The cancel operation was not completed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //FC-8 Fill an order.
        private void btnFillOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Create command and identify it as a stored procedure.
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);
                cmdFillOrder.CommandType = CommandType.StoredProcedure;

                // Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;

                //Add the second input parameter.
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;

                //try-catch-finally
                try
                {
                    //Open the connection.
                    conn.Open();

                    //Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The fill operation was not completed.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-9 Verify that OrderID is ready.
        private bool isOrderID()
        {

            //Check for input in the Order ID text box.
            if (txtOrderID.Text == "")
            {
                MessageBox.Show("Please specify the Order ID.");
                return false;
            }

            // Check for characters other than integers.
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))
            {
               //Show message and clear input.
                MessageBox.Show("Please specify integers only.");
                txtOrderID.Clear();
                return false;
            }
            else
            {
                //Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text);
                return true;
            }
        }

        //Close the form.
        private void btnFinishUpdates_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' FC-1 More namespaces.
Imports System.Text.RegularExpressions
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class FillOrCancel
        Inherits Form
        ' FC-2 Storage for OrderID.
        Private parsedOrderID As Integer

        ' FC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' FC-4 Find an order.
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click

            ' FC-5 Prepare the connection and the command.

            If isOrderID() Then
                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Define the query string that has a parameter for orderID.
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"

                ' Create a SqlCommand object.
                Dim cmdOrderID As New SqlCommand(sql, conn)

                ' Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' FC-6 Run the command and display the results.
                    ' Open connection.
                    conn.Open()

                    ' Run the command by using SqlDataReader.
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()

                    ' Create a data table to hold the retrieved data.
                    Dim dataTable As New DataTable()

                    ' Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr)

                    ' Display the data from the data table in the data grid view.
                    Me.dgvCustomerOrders.DataSource = dataTable

                    ' Close the SqlDataReader.
                    rdr.Close()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-7 Cancel an order.
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create the command and identify it as a stored procedure.
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)
                cmdCancelOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The cancel operation was not completed.")
                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-8 Fill an order.
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create command and identify it as a stored procedure.
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)
                cmdFillOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID

                ' Add second input parameter.
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The fill operation was not completed.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-9 Verify that OrderID is ready.
        Private Function isOrderID() As Boolean

            ' Check for input in the Order ID text box.
            If txtOrderID.Text = "" Then
                MessageBox.Show("Please specify the Order ID.")
                Return False

                ' Check for characters other than integers.
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then

                ' Show message and clear input.
                MessageBox.Show("Please specify integers only.")
                txtOrderID.Clear()
                Return False

            Else
                ' Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text)
                Return True

            End If
        End Function

        ' Close the form.
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click
            Me.Close()
        End Sub
    End Class
End Namespace
```

|Комментировать|Описание|
|-------------|-----------------|
|FC-1|Добавьте `System.Data.SqlClient` , `System.Configuration` и `System.Text.RegularExpressions` в список пространств имен.|
|FC-2|Объявление переменной `parsedOrderID`.|
|FC-3|Вызов метода `GetConnectionString` для получения строки подключения из файла конфигурации приложения и сохранение значения в строковую переменную `connstr`.|
|FC-4|Добавление кода в обработчик события нажатия кнопки `btnFindOrderByID`.|
|FC-5|Эти задачи необходимо выполнить перед попыткой выполнения инструкции SQL или хранимой процедуры.<br /><br /> — Создание `SqlConnection` объекта.<br />— Определите инструкцию SQL или укажите имя хранимой процедуры. (В этом случае вам потребуется выполнить инструкцию `SELECT`.)<br />— Создание `SqlCommand` объекта.<br />— Определите любые параметры для инструкции SQL или хранимой процедуры.|
|FC-6|Этот код использует `SqlDataReader` и `DataTable` для получения и отображения результата запроса.<br /><br /> — Откройте подключение.<br />— Создайте `SqlDataReader` объект, `rdr` выполнив `ExecuteReader` метод для `cmdOrderID` .<br />— Создайте `DataTable` объект для хранения извлеченных данных.<br />— Загрузка данных из `SqlDataReader` объекта в `DataTable` объект.<br />— Отображение данных в представлении сетки данных путем указания `DataTable` в качестве `DataSource` для представления сетки данных.<br />— Закрыть `SqlDataReader` .|
|FC-7|Добавление кода в обработчик события нажатия кнопки `btnCancelOrder`. Этот код выполняет хранимую процедуру `Sales.uspCancelOrder`.|
|FC-8|Добавление кода в обработчик события нажатия кнопки `btnFillOrder`. Этот код выполняет хранимую процедуру `Sales.uspFillOrder`.|
|FC-9|Создайте метод, чтобы убедиться, что `OrderID` готов к отправке в качестве параметра в `SqlCommand` объект.<br /><br /> — Убедитесь, что идентификатор введен в `txtOrderID` .<br />— Используется `Regex.IsMatch` для определения простой проверки нецелочисленных символов.<br />— Переменная была объявлена `parsedOrderID` в FC-2.<br />— Если входные данные допустимы, преобразуйте текст в целое число и сохраните значение в `parsedOrderID` переменной.<br />— Заключите `isOrderID` метод вокруг `btnFindByOrderID` , `btnCancelOrder` и `btnFillOrder` щелкните обработчики событий.|

## <a name="test-your-application"></a><a name="BKMK_testyourapplication"></a> Тестирование приложения
 Нажмите клавишу F5 для сборки и тестирования приложения после написания кода для каждого обработчика события нажатия кнопки и общего кода программы.
