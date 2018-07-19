---
title: Создание приложения простой данных с помощью ADO.NET в Visual Studio
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f44264eace04475fc96e42b533a288ef87dd2c2b
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758487"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Создание приложения простой данных с помощью ADO.NET

При создании приложения, которое работает в базе данных, можно выполнять основные задачи, такие как определение строк подключения, вставка данных и выполнения хранимых процедур. Перечисленные в этом разделе, вы можете узнать, как взаимодействовать с базой данных из простого приложения Windows Forms «формы поверх данных» с помощью Visual C# или Visual Basic и ADO.NET.  Все технологии данных .NET, включая наборы данных, LINQ to SQL и Entity Framework — в конечном счете выполните действия, которые очень похожи тем, что показано в этой статье.

 В этой статье демонстрируется простой способ получить данные из базы данных в виде быстро. Если приложению для изменения данных без того нетривиальные способами и обновления базы данных, можно с помощью Entity Framework и привязка данных к автоматически синхронизировать элементы управления пользовательского интерфейса для изменения базовых данных.

> [!IMPORTANT]
> Чтобы не усложнять код, он не включает обработку исключений для производства.

## <a name="prerequisites"></a>Предварительные требования

Для создания приложения вам потребуются следующие компоненты.

-   Visual Studio.

-   SQL Server Express LocalDB. Если у вас нет SQL Server Express LocalDB, его можно установить с [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

В этом разделе предполагается, что вы знакомы с базовыми функциями интегрированной среды разработки Visual Studio и можно создать приложение Windows Forms, добавить формы в проект, добавить кнопки и другие элементы управления в формах, набор свойств элементов управления, и код для простых событий. Если вам неудобно решать эти задачи, мы рекомендуем выполнить [Приступая к работе с Visual C# и Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) раздел, прежде чем приступать к этому руководству.

## <a name="set-up-the-sample-database"></a>Настройка образца базы данных

Создание образца базы данных, выполнив следующие действия:

1. В Visual Studio откройте **обозревателя серверов** окна.

2. Щелкните правой кнопкой мыши **подключения к данным** и выберите **создать новую базу данных SQL Server**.

3. В **имя_сервера** текста введите **(localdb) \mssqllocaldb**.

4. В **новое имя базы данных** текста введите **Sales**, затем выберите **ОК**.

     Пустой **Sales** базы данных создается и добавляется к узлу подключения к данным в обозревателе серверов.

5. Щелкните правой кнопкой мыши **Sales** подключения данных и нажмите кнопку **новый запрос**.

     Откроется окно редактора запросов.

6. Копировать [сценарий продаж Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) в буфер обмена.

7. Вставьте сценарий T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

     Через некоторое время выполнения запроса отобразятся и создания объектов базы данных. База данных содержит две таблицы: клиенты и заказы. Эти таблицы не содержат данных изначально, но вы можете добавить данные, при запуске приложения, которое будет создано. База данных также содержит четыре простых хранимых процедур.

## <a name="create-the-forms-and-add-controls"></a>Создание форм и добавление элементов управления

1.  Создание проекта для приложения Windows Forms и назовите его **SimpleDataApp**.

     Visual Studio создаст проект и несколько файлов, включая пустую форму Windows с именем **Form1**.

2.  Добавьте в проект две формы Windows, таким образом, чтобы он включал три формы и назначьте им следующие имена:

    -   **Навигация**

    -   **NewCustomer**

    -   **FillOrCancel**

3.  Для каждой формы добавьте текстовые поля, кнопки и другие элементы управления, которые отображаются на рисунках ниже. Для каждого элемента управления задайте свойства, указанные в таблицах.

    > [!NOTE]
    >  Элементы управления "группа" и "надпись" обеспечивают большую ясность, но не используются в коде.

 **Форма навигации**

 ![Диалоговое окно "Навигация"](../data-tools/media/simpleappnav.png)

|Элементы управления формы навигации|Свойства|
|--------------------------------------|----------------|
|Кнопка|Name = btnGoToAdd|
|Кнопка|Name = btnGoToFillOrCancel|
|Кнопка|Name = btnExit|

 **Форма NewCustomer**

 ![Добавление нового заказчика и размещение заказа](../data-tools/media/simpleappnewcust.png)

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

 ![заполнение или отмена заказов](../data-tools/media/simpleappcancelfill.png)

|Элементы управления формы FillOrCancel|Свойства|
|----------------------------------------|----------------|
|TextBox|Name = txtOrderID|
|Кнопка|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Кнопка|Name = btnCancelOrder|
|Кнопка|Name = btnFillOrder|
|Кнопка|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Сохранение строки подключения
 Когда приложение пытается открыть подключение к базе данных, оно должно иметь доступ к строке подключения. Чтобы избежать ручного ввода строки в каждой форме, хранить строки в *App.config* файла в проекте и создать метод, который возвращает строку, при вызове метода из любой формы в приложении.

 Строку подключения можно найти, щелкнув правой кнопкой мыши **Sales** подключение к данным в **обозревателя серверов** и выбрав **свойства**. Найдите **ConnectionString** свойства, затем с помощью **Ctrl**+**объект**, **Ctrl**+**C**  выберите и скопируйте строку в буфер обмена.

1.  Если вы используете C# в **обозревателе решений**, разверните **свойства** узел проекта, а затем откройте **Settings.settings** файл.
    Если вы используете Visual Basic в **обозревателе решений**, нажмите кнопку **Показать все файлы**, разверните **Мой проект** узел, а затем откройте **Settings.settings** файл.

2.  В **имя** столбца, введите `connString`.

3.  В **тип** выберите **(строка подключения)**.

4.  В **область** выберите **приложения**.

5.  В **значение** столбца, введите строку подключения (без каких-либо за пределами кавычки), а затем сохраните изменения.

> [!NOTE]
> В реальном приложении, следует хранить строку подключения безопасно, как описано в разделе [строки подключения и файлы конфигурации](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Написание кода для форм

Этот раздел содержит краткий обзор того, что делает каждая форма. Он также предоставляет код, который определяет базовую логику, при нажатии кнопки на форме.

### <a name="navigation-form"></a>Форма навигации

Форма навигации открывается при запуске приложения. **Добавить учетную запись** кнопки открывает форму NewCustomer. **Заливки или Отмена заказов** кнопка открывает форму FillOrCancel. **Выхода** кнопки закрывает приложение.

#### <a name="make-the-navigation-form-the-startup-form"></a>Преобразование формы навигации в начальную форму

При использовании C#, в **обозревателе решений**откройте **Program.cs**, а затем измените `Application.Run` строки к этому: `Application.Run(new Navigation());`

Если вы используете Visual Basic в **обозревателе решений**откройте **свойства** выберите **приложения** , а затем выберите  **SimpleDataApp.Navigation** в **Начальная форма** списка.

#### <a name="create-auto-generated-event-handlers"></a>Создание обработчиков событий создан

Дважды щелкните три кнопки в форме навигации для создания пустых методов обработчиков событий. Также двойным щелчком кнопки добавляет автоматически созданный код в файл кода конструктора, позволяющую нажатие кнопки для вызова события.

#### <a name="add-code-for-the-navigation-form-logic"></a>Добавьте код для логики формы навигации

В кодовой странице формы навигации завершение тел методов для три кнопки щелкните обработчики событий как показано в следующем коде.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Форма NewCustomer

При вводе имени клиента, а затем выберите **создать учетную запись** кнопки, форма NewCustomer создает учетную запись клиента и SQL Server возвращает значение идентификатора в качестве нового идентификатора клиента. Затем можно разместить заказ для новой учетной записи, указав количество и дату заказа и выбрав **заказать** кнопки.

#### <a name="create-auto-generated-event-handlers"></a>Создание обработчиков событий создан

Создать, щелкните пустой обработчик событий для каждой кнопки в форме NewCustomer, дважды щелкнув каждый из четырех кнопок. Также двойным щелчком кнопки добавляет автоматически созданный код в файл кода конструктора, позволяющую нажатие кнопки для вызова события.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Добавьте код для логики формы NewCustomer

Чтобы выполнить логику формы NewCustomer, выполните следующие действия.

1. Перевести `System.Data.SqlClient` пространства имен в область таким образом, нет необходимости полностью уточнить имена его членов.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Добавьте некоторые переменные и вспомогательные методы в класс, как показано в следующем коде.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Завершение тел методов для четыре кнопки, щелкните обработчики событий как показано в следующем коде.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Форма FillOrCancel

Форма FillOrCancel выполняет запрос на возврат заказа при вводе идентификатора заказа и нажатии **Find Order** кнопки. Возвращенная строка отображается в сетке данных только для чтения. Можно пометить заказ как отмененные (X), при выборе **отменить заказ** кнопки, или можно пометить заказ как выполненный (F) при выборе **Fill Order** кнопки. При выборе **Find Order** кнопку еще раз, появится обновленная строка.

#### <a name="create-auto-generated-event-handlers"></a>Создание обработчиков событий создан

Создайте пустые обработчики события нажатия для четырех кнопок в форму FillOrCancel двойным щелчком кнопки. Также двойным щелчком кнопки добавляет автоматически созданный код в файл кода конструктора, позволяющую нажатие кнопки для вызова события.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Добавьте код для логики форму FillOrCancel

Чтобы выполнить логику форму FillOrCancel, выполните следующие действия.

1. Ввести следующие два пространства имен в область действия, таким образом, нет необходимости использовать полные имена их элементов.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Добавьте переменную и вспомогательный метод к классу, как показано в следующем коде.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Завершение тел методов для четыре кнопки, щелкните обработчики событий как показано в следующем коде.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Тестирование приложения

Выберите **F5** Чтобы выполнить сборку и тестирование приложения после кода каждый обработчик событий нажатия, а затем, после его написания.

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
