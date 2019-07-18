---
title: Создание приложения простой данных с помощью ADO.NET | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70fca5b1329dc9091e0672b41de0798d93aba01a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705168"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Создание простого приложения для работы с данными с помощью ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании приложения, которое работает с данными в базе данных, необходимо выполнить такие основные задачи, как определение строк подключения, вставка данных и выполнение хранимых процедур. Перечисленные в этом разделе, вы можете узнать, как взаимодействовать с базой данных из простого приложения Windows Forms «формы поверх данных» с помощью Visual C# или Visual Basic и ADO.NET.  Все технологии данных .NET, включая наборы данных, LINQ to SQL и Entity Framework — в конечном счете выполните действия, которые очень похожи тем, что показано в этой статье.  
  
 В этой статье демонстрируется простой способ получить данные из базы данных в виде очень быстро. Если приложению для изменения данных без того нетривиальные способами и обновления базы данных, можно с помощью Entity Framework и привязка данных к автоматически синхронизировать элементы управления пользовательского интерфейса для изменения базовых данных.  
  
> [!IMPORTANT]
> С целью упрощения код не включает обработку исключений для выполнения в рабочей среде.  
  
 **Содержание раздела**  
  
- [Настройка образца базы данных](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
- [Создание форм и добавление элементов управления](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
- [Store строку подключения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
- [Получить строку подключения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
- [Написание кода для формы](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
- [Тестирование приложения](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для создания приложения вам потребуются следующие компоненты.  
  
- Visual Studio Community Edition.  
  
- SQL Server Express LocalDB.  
  
- Небольшой пример базы данных, создать, выполнив действия, описанные в [создать базу данных SQL с помощью сценария](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
- Строка подключения для базы данных после ее настройки. Это значение можно найти, открыв **обозреватель объектов SQL Server**, открыв контекстное меню для базы данных, выбрав **свойства**, а затем прокрутите список до **ConnectionString** свойство.  
  
  В рамках этого раздела предполагается, что вы уже знакомы с основными функциями интегрированной среды разработки Visual Studio и можете создать приложение Windows Forms, добавить формы в проект, добавить кнопки и другие элементы управления в формы, задать свойства для этих элементов управления и создать код для простых событий. Если вам неудобно решать эти задачи, мы рекомендуем выполнить [Приступая к работе с Visual C# и Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) перед началом в этом разделе.  
  
## <a name="BKMK_setupthesampledatabase"></a> Настройка образца базы данных  
 Пример базы данных для этого пошагового руководства состоит из таблиц клиентов и заказов. Изначально таблицы не содержат данные, однако вы добавите данные при выполнении созданного приложения. База данных также имеет пять простых хранимых процедур. [Создание базы данных SQL с помощью скрипта](../data-tools/create-a-sql-database-by-using-a-script.md) содержит скрипт Transact-SQL, который создает таблицы, первичные и внешние ключи, ограничения и хранимые процедуры.  
  
## <a name="BKMK_createtheformsandaddcontrols"></a> Создание форм и добавление элементов управления  
  
1. Создание проекта для приложения Windows Forms и назовите его SimpleDataApp.  
  
    Visual Studio создает проект и несколько файлов, включая пустую форму Windows Forms с именем Form1.  
  
2. Добавьте две формы Windows Forms в проект, чтобы он включал три формы, и назначьте им следующие имена:  
  
   - Навигация  
  
   - NewCustomer  
  
   - FillOrCancel  
  
3. Для каждой формы добавьте текстовые поля, кнопки и другие элементы управления, которые отображаются на рисунках ниже. Для каждого элемента управления задайте свойства, указанные в таблицах.  
  
   > [!NOTE]
   > Элементы управления "группа" и "надпись" обеспечивают большую ясность, но не используются в коде.  
  
   **Форма навигации**  
  
   ![Диалоговое окно перехода](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Элементы управления формы навигации|Свойства|  
|--------------------------------------|----------------|  
|Кнопка|Name = btnGoToAdd|  
|Кнопка|Name = btnGoToFillOrCancel|  
|Кнопка|Name = btnExit|  
  
 **Форма NewCustomer**  
  
 ![Добавление нового заказчика и размещение заказа](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
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
  
 ![Заполнение или Отмена заказов](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Элементы управления формы FillOrCancel|Свойства|  
|----------------------------------------|----------------|  
|TextBox|Name = txtOrderID|  
|Кнопка|Name = btnFindByOrderID|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|  
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|  
|Кнопка|Name = btnCancelOrder|  
|Кнопка|Name = btnFillOrder|  
|Кнопка|Name = btnFinishUpdates|  
  
## <a name="BKMK_storetheconnectionstring"></a> Store строку подключения  
 Когда приложение пытается открыть подключение к базе данных, оно должно иметь доступ к строке подключения. Чтобы избежать ручного ввода строки в каждой форме, сохраните строку в файле конфигурации приложения в проекте и создать метод, который возвращает строку, при вызове метода из любой формы в приложении.  
  
 Можно найти строку подключения в **обозреватель объектов SQL Server** , щелкнув правой кнопкой мыши базу данных и выбрав пункт **свойства**, а затем поиск свойства ConnectionString. Используйте сочетание клавиш Ctrl + A, чтобы выбрать строку.  
  
1. В **обозревателе решений**выберите **свойства** в узле проекта, а затем выберите **Settings.settings**.  
  
2. В **имя** столбца, введите `connString`.  
  
3. В **тип** выберите **(строка подключения)**.  
  
4. В **область** выберите **приложения**.  
  
5. В **значение** столбца, введите строку подключения (без каких-либо за пределами кавычки), а затем сохраните изменения.  
  
> [!NOTE]
> В реальном приложении, следует хранить строку подключения безопасно, как описано в разделе [строки подключения и файлы конфигурации](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).  
  
## <a name="BKMK_retrievetheconnectionstring"></a> Получить строку подключения  
  
1. В строке меню выберите **проекта** > **добавить ссылку на**, а затем добавьте ссылку на файл System.Configuration.dll.  
  
2. В строке меню выберите **проекта** > **Добавление класса** добавьте файл класса в проект и назовите файл `Utility`.  
  
     Visual Studio создает файл и отображает его в **обозревателе решений**.  
  
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
  
    |Комментарий|Описание|  
    |-------------|-----------------|  
    |Util-1|Добавление пространства имен `System.Configuration`|  
    |Util-2|Определение переменной `returnValue` и ее инициализация значением `null` (C#) или `Nothing` (Visual Basic).|  
    |Util-3|Несмотря на то, что вы ввели `connString` как имя строки подключения в **свойства** окно, необходимо указать `"SimpleDataApp.Properties.Settings.connString"` (C#) или `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) в коде.|  
  
## <a name="BKMK_writethecodefortheforms"></a> Написание кода для формы  
 Этот раздел содержит краткий обзор функций каждой формы и примеры кода для создания форм. Нумерованные комментарии указывают разделы кода.  
  
### <a name="navigation-form"></a>Форма навигации  
 Форма навигации открывается при запуске приложения. Кнопка **Добавить учетную запись** открывает форму NewCustomer. Кнопка **Выполнение или отмена заказов** открывает форму FillOrCancel. Кнопка **Выход** закрывает приложение.  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>Преобразование формы навигации в начальную форму  
 Если вы используете C# в **обозревателе решений**, откройте файл Program.cs и измените `Application.Run` строки к этому: `Application.Run(new Navigation());`  
  
 Если вы используете Visual Basic в **обозревателе решений**откройте **свойства** выберите **приложения** , а затем выберите  **SimpleDataApp.Navigation** в **Начальная форма** списка.  
  
#### <a name="create-event-handlers"></a>Создание обработчиков событий  
 Дважды щелкните три кнопки на форме, чтобы создать методы пустой обработчик событий.  
  
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
 При вводе имени клиента, а затем выберите **создать учетную запись** кнопки, форма NewCustomer создает учетную запись клиента и SQL Server возвращает значение идентификатора в качестве номера новой учетной записи. Затем вы размещаете заказ для новой учетной записи, указав количество и дату заказа и выбрав **заказать** кнопки.  
  
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
  
|Комментарий|Описание|  
|-------------|-----------------|  
|NC-1|Добавить `System.Data.SqlClient` и `System.Configuration` в список пространств имен.|  
|NC-2|Объявление переменных `parsedCustomerID` и `orderID`, которые будут использоваться позже.|  
|NC-3|Вызов метода `GetConnectionString` для получения строки подключения из файла конфигурации приложения и сохранение значения в строковую переменную `connstr`.|  
|NC-4|Добавление кода в обработчик события нажатия кнопки `btnCreateAccount`.|  
|NC-5|Создание оболочки для кода события нажатия кнопки с помощью вызова `isCustomerName`, чтобы процедура `uspNewCustomer` выполнялась только в том случае, если указано имя клиента.|  
|NC-6|Создание объекта `SqlConnection` (`conn`) и передача в строке подключения в `connstr`.|  
|NC-7|Создание объекта `SqlCommand`, `cmdNewCustomer`.<br /><br /> -Укажите `Sales.uspNewCustomer` как следует запускать хранимую процедуру.<br />— Используйте `CommandType` свойство, чтобы указать, что команда является хранимой процедурой.|  
|NC-8|Добавление входного параметра `@CustomerName` из хранимой процедуры.<br /><br /> -Добавьте параметр `Parameters` коллекции.<br />— Используйте `SqlDbType` перечисление, чтобы указать тип параметра как nvarchar(40).<br />-Укажите `txtCustomerName.Text` как источник.|  
|NC-9|Добавление выходного параметра из хранимой процедуры.<br /><br /> -Добавьте параметр `Parameters` коллекции.<br />— Используйте `ParameterDirection.Output` определить параметр как выходной.|  
|NC-10|Добавьте блок Try-Catch-Finally для открытия подключения, выполните хранимую процедуру, обработки исключений и затем закрывает его.|  
|NC-11|Открытие подключения (`conn`), созданного в шаге NC-6.|  
|NC-12|Используйте `ExecuteNonQuery` метод `cmdNewCustomer` для запуска `Sales.uspNewCustomer` хранимой процедуры. Эта хранимая процедура запускается `INSERT` инструкции, а не запрос.|  
|NC-13|Значение `@CustomerID` возвращается как значение идентификатора из базы данных. Поскольку это целое число, вам придется преобразовать его в строку для отображения на **Customer ID** текстовое поле.<br /><br /> -Вы объявили `parsedCustomerID` в шаге NC-2.<br />-Store `@CustomerID` значение в `parsedCustomerID` для последующего использования.<br />-Преобразуйте возвращенный идентификатор клиента в строку и вставьте ее в `txtCustomerID.Text`.|  
|NC-14|Для этого примера добавьте простое предложение catch (не рабочего уровня).|  
|NC-15|Всегда закрывайте подключение, после того как закончите его использование, чтобы его можно было вернуть в пул подключений. См. в разделе [пул (ADO.NET) соединение с SQL Server](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC-16|Определите метод для проверки наличия имени клиента.<br /><br /> — Если текстовое поле не заполнено, выводит сообщение и возвращать `false`, так как необходимо указать имя, чтобы создать учетную запись.<br />– Если текстовое поле не является пустым, возвращается `true`.|  
|NC-17|Добавление кода в обработчик события нажатия кнопки `btnPlaceOrder`.|  
|NC-18|Создание оболочки для кода события `btnPlaceOrder_Click` путем вызова `isPlaceOrderReady`, чтобы процедура `uspPlaceNewOrder` не выполнялась, если отсутствуют необходимые входные данные.|  
|С NC-19 по NC-25|Эти фрагменты кода напоминают код, добавленный для обработчика событий `btnCreateAccount_Click`.<br /><br /> -   NC-19. Создание объекта `SqlCommand`, `cmdNewOrder` и задание `Sales.uspPlaceOrder` в качестве хранимой процедуры.<br />-NC-20 по NC-23 — входные параметры для хранимой процедуры.<br />-   NC-24. `@RC` будет содержать возвращаемое значение, которое представляет идентификатор созданного заказа из базы данных. Направление этого параметра указывается как `ReturnValue`.<br />-   NC-25. Сохранение значения идентификатора заказа в переменной `orderID`, объявленной в шаге NC-2, и отображение значения в окне сообщения.|  
|NC-26|Определение метода для проверки того, что идентификатор клиента существует и в поле `numOrderAmount` указано количество.|  
|NC-27|Вызов метода `ClearForm` в обработчике события нажатия кнопки `btnAddAnotherAccount`.|  
|NC-28|Создание метода `ClearForm` для сброса значений в форме, если требуется добавить другого клиента.|  
|NC-29|Закрытие формы NewCustomer и возврат фокуса в форму навигации.|  
  
### <a name="fillorcancel-form"></a>Форма FillOrCancel  
 Форма FillorCancel выполняет запрос на возврат заказа при вводе идентификатора заказа и выборе **Find Order** кнопки. Возвращенная строка отображается в сетке данных только для чтения. Можно пометить заказ как отмененные (X), при выборе **отменить заказ** кнопки, или можно пометить заказ как выполненный (F) при выборе **Fill Order** кнопки. При выборе **Find Order** кнопку еще раз, появится обновленная строка.  
  
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
  
|Комментарий|Описание|  
|-------------|-----------------|  
|FC-1|Добавить `System.Data.SqlClient`, `System.Configuration`, и `System.Text.RegularExpressions` в список пространств имен.|  
|FC-2|Объявление переменной `parsedOrderID`.|  
|FC-3|Вызов метода `GetConnectionString` для получения строки подключения из файла конфигурации приложения и сохранение значения в строковую переменную `connstr`.|  
|FC-4|Добавление кода в обработчик события нажатия кнопки `btnFindOrderByID`.|  
|FC-5|Эти задачи необходимо выполнить перед попыткой выполнения инструкции SQL или хранимой процедуры.<br /><br /> -Создание `SqlConnection` объекта.<br />-Задать инструкцию SQL или укажите имя хранимой процедуры. (В этом случае вам потребуется выполнить инструкцию `SELECT`.)<br />-Создание `SqlCommand` объекта.<br />-Определите параметры для инструкции SQL или хранимой процедуры.|  
|FC-6|Этот код использует `SqlDataReader` и `DataTable` для получения и отображения результата запроса.<br /><br /> -Открытия подключения.<br />-Создание `SqlDataReader` объекта, `rdr`, запустив `ExecuteReader` метод для `cmdOrderID`.<br />-Создание `DataTable` объект для хранения полученных данных.<br />-Загрузка данных из `SqlDataReader` в коллекцию `DataTable` объекта.<br />— Отображение данных в представлении в виде сетки данных путем указания `DataTable` как `DataSource` для представления сетки данных.<br />-Закройте `SqlDataReader`.|  
|FC-7|Добавление кода в обработчик события нажатия кнопки `btnCancelOrder`. Этот код выполняет хранимую процедуру `Sales.uspCancelOrder`.|  
|FC-8|Добавление кода в обработчик события нажатия кнопки `btnFillOrder`. Этот код выполняет хранимую процедуру `Sales.uspFillOrder`.|  
|FC-9|Создайте метод, чтобы убедиться, что `OrderID` готов для отправки в качестве параметра `SqlCommand` объекта.<br /><br /> -Убедитесь в том, что идентификатор был введен в `txtOrderID`.<br />— Используйте `Regex.IsMatch` для определения простой проверки нецелочисленных символов.<br />-Вы объявили `parsedOrderID` переменной FC-2.<br />— Если ввод был допустимым, преобразования текста в целое число и сохраните значение в `parsedOrderID` переменной.<br />-Wrap `isOrderID` метод вокруг `btnFindByOrderID`, `btnCancelOrder`, и `btnFillOrder` обработчики события нажатия.|  
  
## <a name="BKMK_testyourapplication"></a> Тестирование приложения  
 Выберите клавишу F5, чтобы создавать и тестировать приложения после кода каждый обработчик событий нажатия, а затем, после его написания.
