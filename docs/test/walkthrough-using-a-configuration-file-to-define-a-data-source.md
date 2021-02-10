---
title: Использование файла конфигурации для определения источника данных
description: Сведения о том, как использовать источник данных, определенный в файле app.config, для модульного тестирования, в том числе о создании такого файла с определением источника данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f234d0285f5a0ed01567bb77c21e4c2d080a5f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967882"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Пошаговое руководство. Использование файла конфигурации для определения источника данных

В этом пошаговом руководстве демонстрируется использование источника данных, определенного в файле *app.config*, для модульного тестирования. Вы узнаете, как создать файл *app.config*, определяющий источник данных, который может использоваться классом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>. В данном пошаговом руководстве представлены следующие задачи:

- создание файла *app.config*;

- определение настраиваемого раздела конфигурации;

- определение строк подключения;

- определение источников данных;

- доступ к источникам данных с помощью класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

## <a name="prerequisites"></a>Предварительные требования

Для выполнения данного пошагового руководства требуется:

- Visual Studio Enterprise

- Microsoft Access или Microsoft Excel для предоставления данных хотя бы для одного из методов теста;

- решение Visual Studio, содержащее тестовый проект.

## <a name="add-an-appconfig-file-to-the-project"></a>Добавление к проекту файла app.config

1. Если файл *app.config* уже существует в тестовом проекте, переходите к разделу [Определение настраиваемого раздела конфигурации](#define-a-custom-configuration-section).

2. Щелкните тестовый проект правой кнопкой мыши в **обозревателе решений** и выберите **Добавить** > **Новый элемент**.

     Откроется окно **Добавление нового элемента**.

3. Выберите шаблон **Файл конфигурации приложения** и нажмите кнопку **Добавить**.

## <a name="define-a-custom-configuration-section"></a>Определение настраиваемого раздела конфигурации

Просмотрите файл *app.config*. Он содержит как минимум объявление XML и корневой элемент.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Добавление настраиваемого раздела конфигурации в файл app.config

1. Корневым элементом файла *app.config* должен быть элемент **configuration**. Создайте элемент **configSections** в элементе **configuration**. **configSections** должен быть первым элементом в файле *app.config*.

2. В элементе **configSections** создайте элемент **section**.

3. В элементе **section** добавьте атрибут с именем `name` и задайте для него значение `microsoft.visualstudio.testtools`. Добавьте еще один атрибут с именем `type` и задайте для него значение `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`.

Элемент **section** должен принять следующий вид:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Имя сборки должно соответствовать версии, которую вы используете.

## <a name="define-connection-strings"></a>Определение строк подключения

Строки подключения определяют сведения, относящиеся к конкретному поставщику, для доступа к источникам данных. Строки подключения, определенные в файлах конфигурации, предоставляют сведения о поставщике данных для повторного использования в приложении. В этом разделе создайте две строки подключения, которые будут использоваться источниками данных, определенными в настраиваемом разделе конфигурации.

### <a name="to-define-connection-strings"></a>Определение строк подключения

1. После элемента **configSections** создайте элемент **connectionStrings**.

2. В элементе **connectionStrings** создайте два элемента **add**.

3. В первом элементе **add** создайте следующие атрибуты и значения для подключения к базе данных Microsoft Access:

|attribute|Значения|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

Во втором элементе **add** создайте следующие атрибуты и значения для подключения к таблице Microsoft Excel:

|attribute|Значения|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

Элемент **connectionStrings** должен принять следующий вид:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Определение источников данных

Раздел источников данных содержит четыре атрибута, которые используются тестовой подсистемой для получения данных из источника данных.

- `name` определяет удостоверение, используемое <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> для указания источника данных для использования.

- `connectionString` определяет строку подключения, созданную в предыдущем разделе "Определение строк подключения".

- `dataTableName` определяет таблицу или лист, которые содержат данные, используемые в тесте.

- `dataAccessMethod` определяет способ доступа к значениям данных в источнике данных.

В этом разделе мы определим два источника данных для использования в модульном тесте.

### <a name="to-define-data-sources"></a>Определение источников данных

1. После элемента **connectionStrings** создайте элемент **microsoft.visualstudio.testtools**. Этот раздел файла был создан в разделе "Определение настраиваемого раздела конфигурации".

2. В элементе **microsoft.visualstudio.testtools** создайте элемент **dataSources**.

3. В элементе **dataSources** создайте два элемента **add**.

4. В первом элементе **add** создайте следующие атрибуты и значения для источника данных Microsoft Access:

|attribute|Значения|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

Во втором элементе **add** создайте следующие атрибуты и значения для источника данных Microsoft Excel:

|attribute|Значения|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

Элемент **microsoft.visualstudio.testtools** должен принять следующий вид:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Окончательный файл *app.config* должен принять следующий вид:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Создание модульного теста, использующего источники данных, определенные в файле app.config

Определив файл *app.config*, мы создадим модульный тест, использующий данные, находящиеся в источниках данных, которые определены в файле *app.config*. В этом разделе мы рассмотрим:

- создание источников данных, определенных в файле *app.config*;

- использование источников данных в двух методах теста, сравнивающих значения в каждом источнике данных.

### <a name="to-create-a-microsoft-access-data-source"></a>Создание источника данных Microsoft Access

1. Создайте файл базы данных Microsoft Access с именем *testdatasource.accdb*.

2. Создайте таблицу с именем `MyDataTable` в *testdatasource.accdb*.

3. Создайте два поля в таблице `MyDataTable` с именем `Arg1` и `Arg2`, используя тип данных `Number`.

4. Добавьте пять сущностей в таблицу `MyDataTable` со следующими значениями для `Arg1` и `Arg2` соответственно: (10,50), (3,2), (6,0), (0,8) и (12312,1000).

5. Сохраните и закройте базу данных.

6. Измените строку подключения так, чтобы она указывала на расположение базы данных. Измените значение `Data Source` так, чтобы оно отражало расположение базы данных.

### <a name="to-create-a-microsoft-excel-data-source"></a>Создание источника данных Microsoft Excel

1. Создайте электронную таблицу Microsoft Excel с именем *data.xlsx*.

2. Создайте лист с именем `Sheet1`, если он еще не существует в *data.xlsx*.

3. Создайте на листе `Sheet1` два заголовка столбцов и назовите их `Val1` и `Val2`.

4. Добавьте пять сущностей в таблицу `Sheet1` со следующими значениями для `Val1` и `Val2` соответственно: (1,1), (2,2), (3,3), (4,4) и (5,0).

5. Сохраните и закройте таблицу.

6. Измените строку подключения так, чтобы она указывала на расположение таблицы. Измените значение `dbq` так, чтобы оно отражало расположение таблицы.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Создание модульного теста с помощью источников данных файла app.config

1. Добавьте модульный тест в тестовый проект.

2. Замените автоматически созданное содержимое модульного теста следующим кодом.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. Проверьте атрибуты DataSource. Обратите внимание на имена параметров из файла *app.config*.

4. Выполните построение решения и запустите тесты MyTestMethod и MyTestMethod2.

> [!IMPORTANT]
> Разверните элементы как источники данных, чтобы они были доступны для теста в каталоге развертывания.

## <a name="see-also"></a>См. также

- [Модульное тестирование кода](../test/unit-test-your-code.md)
- [Практическое руководство. Создание модульного теста, управляемого данными](../test/how-to-create-a-data-driven-unit-test.md)
