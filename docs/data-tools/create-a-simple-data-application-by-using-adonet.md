---
title: "Пошаговое руководство. Создание простого приложения для работы с данными с помощью ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 42
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Пошаговое руководство. Создание простого приложения для работы с данными с помощью ADO.NET
При создании приложения, которое работает с данными в базе данных, необходимо выполнить такие основные задачи, как определение строк подключения, вставка данных и выполнение хранимых процедур.  В этом разделе описывается, как взаимодействовать с базой данных из простого приложения Windows Forms с помощью Visual C\# или Visual Basic и ADO.NET.  
  
> [!IMPORTANT]
>  С целью упрощения код не включает обработку исключений для выполнения в рабочей среде.  
  
 **Содержание раздела**  
  
-   [Настройка образца базы данных](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Создание форм и добавление элементов управления](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Сохранение строки подключения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Получение строки подключения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Написание кода для форм](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Тестирование приложения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## Обязательные компоненты  
 Для создания приложения вам потребуются следующие компоненты.  
  
-   Visual Studio 2012 с обновлением 1 или [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]  
  
-   SQL Server 2012 Express LocalDB  
  
-   Небольшая база данных для примера, которую можно создать, выполнив действия, описанные в разделе [Пошаговое руководство. Создание небольшого примера базы данных](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
-   Строка подключения для базы данных после ее настройки.  Чтобы найти это значение, откройте **обозреватель объектов SQL Server**, откройте контекстное меню для базы данных, выберите **Свойства**, а затем прокрутите список до свойства **Строка подключения**.  
  
 В рамках этого раздела предполагается, что вы уже знакомы с основными функциями интегрированной среды разработки Visual Studio и можете создать приложение Windows Forms, добавить формы в проект, добавить кнопки и другие элементы управления в формы, задать свойства для этих элементов управления и создать код для простых событий.  Если вы не уверены, что справитесь с этими задачами, рекомендуем ознакомиться с [Начало работы с Visual C\# и Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md), прежде чем приступать к процедурам этого раздела.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Настройка образца базы данных  
 Пример базы данных для этого пошагового руководства состоит из таблиц клиентов и заказов.  Изначально таблицы не содержат данные, однако вы добавите данные при выполнении созданного приложения.  База данных также имеет пять простых хранимых процедур.  [Пошаговое руководство. Создание небольшого примера базы данных](../data-tools/create-a-sql-database-by-using-a-script.md) содержит скрипт Transact\-SQL, который создает таблицы, первичные и внешние ключи, ограничения и хранимые процедуры.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Создание форм и добавление элементов управления  
  
1.  Создайте проект для приложения Windows Forms и назовите его `SimpleDataApp`.  
  
     Visual Studio создает проект и несколько файлов, включая пустую форму Windows Forms с именем Form1.  
  
2.  Добавьте две формы Windows Forms в проект, чтобы он включал три формы, и назначьте им следующие имена.  
  
    -   Навигация  
  
    -   NewCustomer  
  
    -   FillOrCancel  
  
3.  Для каждой формы добавьте текстовые поля, кнопки и другие элементы управления, которые отображаются на рисунках ниже.  Для каждого элемента управления задайте свойства, указанные в таблицах.  
  
    > [!NOTE]
    >  Элементы управления "группа" и "надпись" обеспечивают большую ясность, но не используются в коде.  
  
 **Форма навигации**  
  
 ![Диалоговое окно "Навигация"](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Элементы управления формы навигации|Свойства|  
|-----------------------------------------|--------------|  
|Кнопка|Name \= btnGoToAdd|  
|Кнопка|Name \= btnGoToFillOrCancel|  
|Кнопка|Name \= btnExit|  
  
 **Форма NewCustomer**  
  
 ![Добавление нового заказчика и размещение заказа](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|Элементы управления формы NewCustomer|Свойства|  
|-------------------------------------------|--------------|  
|TextBox|Name \= txtCustomerName|  
|TextBox|Name \= txtCustomerID<br /><br /> Readonly \= True|  
|Кнопка|Name \= btnCreateAccount|  
|NumericUpDown|DecimalPlaces \= 0<br /><br /> Maximum \= 5000<br /><br /> Name \= numOrderAmount|  
|DateTimePicker|Format \= Short<br /><br /> Name \= dtpOrderDate|  
|Кнопка|Name \= btnPlaceOrder|  
|Кнопка|Name \= btnAddAnotherAccount|  
|Кнопка|Name \= btnAddFinish|  
  
 **Форма FillOrCancel**  
  
 ![заполнение или отмена заказов](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Элементы управления формы FillOrCancel|Свойства|  
|--------------------------------------------|--------------|  
|TextBox|Name \= txtOrderID|  
|Кнопка|Name \= btnFindByOrderID|  
|DateTimePicker|Format \= Short<br /><br /> Name \= dtpFillDate|  
|DataGridView|Name \= dgvCustomerOrders<br /><br /> Readonly \= True<br /><br /> RowHeadersVisible \= False|  
|Кнопка|Name \= btnCancelOrder|  
|Кнопка|Name \= btnFillOrder|  
|Кнопка|Name \= btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Сохранение строки подключения  
 Когда приложение пытается открыть подключение к базе данных, оно должно иметь доступ к строке подключения.  Чтобы избежать ручного ввода строки в каждой форме, сохраните строку в файле конфигурации приложения в проекте и создайте метод, который возвращает строку при вызове из любой формы в приложении.  
  
1.  Откройте контекстное меню проекта и выберите **Свойства**.  
  
2.  В левом столбце окна **Свойства** перейдите на вкладку **Параметры**.  
  
3.  В столбце **Имя** введите `connString`.  
  
4.  В списке **Тип** выберите **\(Строка подключения\)**.  
  
5.  В списке **Область** выберите **Приложение**.  
  
6.  В столбце **Значение** введите строку подключения и сохраните изменения.  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Получение строки подключения  
  
1.  В строке меню выберите **Проект**, **Добавить ссылку**, а затем добавьте ссылку на файл System.Configuration.dll.  
  
2.  В строке меню выберите **Проект**, **Добавить класс**, добавьте файл класса в проект и назовите файл `Utility`.  
  
     Visual Studio создаст файл и выведет его в **обозревателе решений**.  
  
3.  В файле Utility замените код\-заполнитель следующим кодом.  Обратите внимание на нумерованные комментарии \(с префиксом Util\-\), которые указывают разделы кода.  В таблице под примером кода описаны ключевые моменты.  
  
    ```c#  
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
  
    |Примечание|Описание|  
    |----------------|--------------|  
    |Util\-1|Добавление пространства имен System.Configuration.|  
    |Util\-2|Определение переменной `returnValue` и ее инициализация значением `null` \(C\#\) или `Nothing` \(Visual Basic\).|  
    |Util\-3|Несмотря на то, что вы ввели `connString` как имя строки подключения в окне **Свойства**, в коде необходимо указать `"SimpleDataApp.Properties.Settings.connString"` \(C\#\) или `"SimpleDataApp.My.MySettings.connString"` \(Visual Basic\).|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Написание кода для форм  
 Этот раздел содержит краткий обзор функций каждой формы и примеры кода для создания форм.  Нумерованные комментарии указывают разделы кода.  
  
### Форма навигации  
 Форма навигации открывается при запуске приложения.  Кнопка **Add an account** \(Добавить учетную запись\) открывает форму NewCustomer.  Кнопка **Fill or cancel orders** \(Выполнение или отмена заказов\) открывает форму FillOrCancel.  Кнопка **Exit** \(Выход\) закрывает приложение.  
  
#### Преобразование формы навигации в начальную форму  
 При использовании C\# в **обозревателе решений** откройте файл Program.cs и измените строку `Application.Run` на следующую: `Application.Run(new Navigation());`.  
  
 При использовании Visual Basic в **обозревателе решений** откройте окно **Свойства**, перейдите на вкладку **Приложение**, а затем в списке **Начальная форма** выберите SimpleDataApp.Navigation.  
  
#### Создание обработчиков событий  
 Создайте пустые обработчики события нажатия для трех кнопок в форме.  См. раздел [Практическое руководство. Создание обработчиков событий по умолчанию в конструкторе Windows Forms](http://msdn.microsoft.com/ru-ru/757bcc16-1dc2-4d68-b115-ac0f53f05c8d).  
  
#### Создание кода для навигации  
 В форме навигации замените существующий код следующим кодом.  
  
```c#  
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
  
### Форма NewCustomer  
 При вводе имени клиента и нажатии кнопки **Create Account** \(Создать учетную запись\) форма NewCustomer создает учетную запись клиента, а SQL Server возвращает значение идентификатора в качестве номера новой учетной записи.  Затем вы размещаете заказ для новой учетной записи, указав количество и дату заказа и нажав кнопку **Place Order** \(Заказать\).  
  
#### Создание обработчиков событий  
 Создайте пустой обработчик события нажатия для каждой кнопки в форме.  
  
#### Создание кода для NewCustomer  
 Добавьте следующий код в форму NewCustomer.  Пошагово выполните каждый блок кода, используя нумерованные комментарии и таблицу под примером кода.  
  
```c#  
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
  
                //NC-23 @Status. For a new order, the status is always O (open)  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is the orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try – catch - finally  
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
  
        //NC-27 Reset the form for another new account  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls  
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
  
                ' NC-24 add return value for stored procedure, which is the orderID  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try – catch - finally  
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
                    MessageBox.Show("Order could not not be placed.")  
  
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
  
                ' Verify that Amount isn't 0   
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
  
|Примечание|Описание|  
|----------------|--------------|  
|NC\-1|Добавление в список пространств имен System.Data.SqlClient и System.Configuration.|  
|NC\-2|Объявление переменных `parsedCustomerID` и `orderID`, которые будут использоваться позже.|  
|NC\-3|Вызов метода `GetConnectionString` для получения строки подключения из файла конфигурации приложения и сохранение значения в строковую переменную `connstr`.|  
|NC\-4|Добавление кода в обработчик события нажатия кнопки `btnCreateAccount`.|  
|NC\-5|Создание оболочки для кода события нажатия кнопки с помощью вызова `isCustomerName`, чтобы процедура `uspNewCustomer` выполнялась только в том случае, если указано имя клиента.|  
|NC\-6|Создание объекта `SqlConnection` \(`conn`\) и передача в строке подключения в `connstr`.|  
|NC\-7|Создание объекта `SqlCommand`, `cmdNewCustomer`.<br /><br /> -   Укажите `Sales.uspNewCustomer` в качестве хранимой процедуры для выполнения.<br />-   Используйте свойство `CommandType` для указания того, что команда является хранимой процедурой.|  
|NC\-8|Добавление входного параметра `@CustomerName` из хранимой процедуры.<br /><br /> -   Добавьте параметр в коллекцию `Parameters`.<br />-   Чтобы указать тип параметра как nvarchar\(40\), используйте перечисление SqlDbType.<br />-   Укажите `txtCustomerName.Text` в качестве источника.|  
|NC\-9|Добавление выходного параметра из хранимой процедуры.<br /><br /> -   Добавьте параметр в коллекцию `Parameters`.<br />-   Используйте `ParameterDirection.Output`, чтобы идентифицировать параметр как выходной.|  
|NC\-10|Добавление блока try\-catch\-finally для открытия подключения, запуска хранимой процедуры, обработки исключения и закрытия подключения.|  
|NC\-11|Открытие подключения \(`conn`\), созданного в шаге NC\-6.|  
|NC\-12|Использование метода `ExecuteNonQuery` `cmdNewCustomer` для запуска хранимой процедуры `Sales.uspNewCustomer`, которая выполняет инструкцию `INSERT`, а не запрос.|  
|NC\-13|Значение `@CustomerID` возвращается как значение идентификатора из базы данных.  Поскольку это целое число, необходимо преобразовать его в строку для отображения в текстовом поле идентификатора клиента.<br /><br /> -   Вы объявили `parsedCustomerID` в шаге NC\-2.<br />-   Сохраните значение `@CustomerID` в `parsedCustomerID` для последующего использования.<br />-   Преобразуйте возвращенный идентификатор клиента в строку и вставьте ее в `txtCustomerID.Text`.|  
|NC\-14|Для этого примера добавьте простое \(не рабочего уровня\) предложение catch.|  
|NC\-15|Всегда закрывайте подключение, после того как закончите его использование, чтобы его можно было вернуть в пул подключений.  См. статью [SQL Server Connection Pooling \(ADO.NET\)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx) \(Пулы подключений SQL Server \(ADO.NET\)\).|  
|NC\-16|Определите метод для проверки наличия имени клиента.<br /><br /> -   Если текстовое поле не заполнено, выводится сообщение и возвращается значение `false`, так как имя необходимо для создания учетной записи.<br />-   Если текстовое поле не является пустым, возвращается значение `true`.|  
|NC\-17|Добавление кода в обработчик события нажатия кнопки `btnPlaceOrder`.|  
|NC\-18|Создание оболочки для кода события `btnPlaceOrder_Click` путем вызова `isPlaceOrderReady`, чтобы процедура `uspPlaceNewOrder` не выполнялась, если отсутствуют необходимые входные данные.|  
|С NC\-19 по NC\-25|Эти фрагменты кода напоминают код, добавленный для обработчика событий `btnCreateAccount_Click`.<br /><br /> -   NC\-19  Создание объекта `SqlCommand`, `cmdNewOrder` и задание `Sales.uspPlaceOrder` в качестве хранимой процедуры.<br />-   Шаги с NC\-20 по NC\-23 — входные параметры для хранимой процедуры.<br />-   NC\-24  `@RC` будет содержать возвращаемое значение, которое представляет идентификатор созданного заказа из базы данных.  Направление этого параметра указывается как `ReturnValue`.<br />-   NC\-25  Сохранение значения идентификатора заказа в переменной `orderID`, объявленной в шаге NC\-2, и отображение значения в окне сообщения.|  
|NC\-26|Определение метода для проверки того, что идентификатор клиента существует и в поле `numOrderAmount` указано количество.|  
|NC\-27|Вызов метода `ClearForm` в обработчике события нажатия кнопки `btnAddAnotherAccount`.|  
|NC\-28|Создание метода `ClearForm` для сброса значений в форме, если требуется добавить другого клиента.|  
|NC\-29|Закрытие формы NewCustomer и возврат фокуса в форму навигации.|  
  
### Форма FillOrCancel  
 Форма FillOrCancel выполняет запрос на возврат заказа при вводе идентификатора заказа и нажатии кнопки **Find Order** \(Найти заказ\).  Возвращенная строка отображается в сетке данных только для чтения.  Можно пометить заказ как отмененный \(X\) при нажатии кнопки **Cancel Order** \(Отменить заказ\) или как выполненный \(F\) при нажатии кнопки **Fill Order** \(Выполнить заказ\).  При повторном нажатии кнопки **Find Order** появится обновленная строка.  
  
#### Создание обработчиков событий  
 Создайте пустые обработчики события нажатия кнопки для четырех кнопок в форме.  
  
#### Создание кода для FillOrCancel  
 Добавьте следующий код в форму FillOrCancel.  Пошагово выполните блоки кода, используя нумерованные комментарии и таблицу под примером кода.  
  
```c#  
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
            //FC-5 Prepare the connection and the command  
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
  
                //try – catch - finally  
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
  
                    //Display the data from the datatable in the datagridview.  
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
  
                //try – catch - finally  
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
        ' FC-2 Storage for OrderID  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string  
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
  
                    ' Load the data from the SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the datagridview.  
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
  
|Примечание|Описание|  
|----------------|--------------|  
|FC\-1|Добавление в список пространств имен Add System.Data.SqlClient, System.Configuration и System.Text.RegularExpressions.|  
|FC\-2|Объявление переменной `parsedOrderID`.|  
|FC\-3|Вызов метода `GetConnectionString` для получения строки подключения из файла конфигурации приложения и сохранение значения в строковую переменную `connstr`.|  
|FC\-4|Добавление кода в обработчик события нажатия кнопки `btnFindOrderByID`.|  
|FC\-5|Выглядит знакомо?  Эти задачи необходимо выполнить перед попыткой выполнения инструкции SQL или хранимой процедуры.<br /><br /> -   Создайте объект SqlConnection.<br />-   Определите инструкцию SQL или укажите имя хранимой процедуры.  \(В этом случае вам потребуется выполнить инструкцию `SELECT`.\)<br />-   Создание объекта `SqlCommand`.<br />-   Определите параметры инструкции SQL или хранимой процедуры.|  
|FC\-6|Этот код использует `SqlDataReader` и `DataTable` для получения и отображения результата запроса.<br /><br /> -   Откройте подключение.<br />-   Создайте объект SqlDataReader, `rdr`, выполнив метод `ExecuteReader` `cmdOrderID`.<br />-   Создайте объект `DataTable` для хранения полученных данных.<br />-   Загрузите данные из `SqlDataReader` в объект `DataTable`.<br />-   Настройте отображение данных в элементе управления DataGridView, указав `DataTable` в качестве `DataSource` для DataGridView.<br />-   Закройте SqlDataReader.|  
|FC\-7|Добавление кода в обработчик события нажатия кнопки `btnCancelOrder`.  Этот код выполняет хранимую процедуру `Sales.uspCancelOrder`.|  
|FC\-8|Добавление кода в обработчик события нажатия кнопки `btnFillOrder`.  Этот код выполняет хранимую процедуру `Sales.uspFillOrder`.|  
|FC\-9|Создание метода для проверки того, что `OrderID` готов для отправки в качестве параметра в объект `SqlCommand`.<br /><br /> -   Убедитесь, что идентификатор введен в `txtOrderID`.<br />-   Используйте `Regex.IsMatch` для определения простой проверки нецелочисленных символов.<br />-   Вы объявили переменную `parsedOrderID` на шаге FC\-2.<br />-   Если введенные данные допустимы, текст преобразуется в целое число и значение сохраняется в переменной `parsedOrderID`.<br />-   Создайте оболочку для обработчиков события нажатия кнопки `btnFindByOrderID`, `btnCancelOrder` и `btnFillOrder` с помощью метода `isOrderID`.|  
  
##  <a name="BKMK_testyourapplication"></a> Тестирование приложения  
 Нажмите клавишу F5 для сборки и тестирования приложения после написания кода для каждого обработчика события нажатия кнопки и общего кода программы.