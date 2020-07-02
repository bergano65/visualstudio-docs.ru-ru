---
title: Пошаговое руководство. Создание LINQ to SQL классов с помощью наследования одной таблицы (реляционный конструктор) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cf95bd2095d9713d498ddccf68fd1e81e1b1e64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535711"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Пошаговое руководство. Создание классов LINQ to SQL с использованием наследования с одной таблицей (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) поддерживают наследование одной таблицы, так как обычно реализуются в реляционных системах. Это пошаговое руководство раскрывает общие шаги, приведенные в разделе [Практическое руководство. Настройка наследования с помощью конструктора O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) , и предоставляет некоторые реальные данные для демонстрации использования наследования в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 В этом пошаговом руководстве вы будете выполнять следующие задачи:

- Создайте таблицу базы данных и добавьте в нее данные.

- Создайте приложение Windows Forms.

- Добавление файла [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] в проект.

- Создайте новые классы сущностей.

- Конфигурируйте классы сущностей на использование наследования.

- Выполните запрос унаследованного класса.

- Отобразите данные на Windows Forms

## <a name="create-a-table-to-inherit-from"></a>Создайте таблицу в Наследовать из
 Чтобы увидеть, как работает наследование, надо создать небольшую таблицу Person, использовать ее как базовый класс, и затем создать объект Employee, который наследует из него.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Для создания базовой таблицы, чтобы продемонстрировать наследование

1. В **Обозреватель сервера** / **Обозреватель базы данных**щелкните правой кнопкой мыши узел **таблицы** и выберите команду **Добавить новую таблицу**.

    > [!NOTE]
    > Может быть использована база данных Northwind или любая другая, к которой можно добавить таблицу.

2. В Конструкторе таблиц добавьте в таблицу следующие столбцы:

    |Имя столбца|Тип данных|Разрешить значения NULL|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**IsFalse**|
    |**Тип**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**IsFalse**|
    |**LastName**|**nvarchar(200)**|**IsFalse**|
    |**Менеджер**|**int**|**True**|

3. Задайте столбец ID в качестве первичного ключа

4. Сохраните таблицу и дайте ей имя **Person**.

## <a name="add-data-to-the-table"></a>Добавление данных в таблицу
 Чтобы вы могли убедиться, что наследование конфигурировано правильно, в таблицу нужно ввести некоторые данные для каждого класса в наследовании единственной таблицы.

#### <a name="to-add-data-to-the-table"></a>Для добавления данных в таблицу

1. Откройте таблицу в окне просмотра данных. (Щелкните правой кнопкой мыши таблицу **Person** в **Обозреватель сервера** / **Обозреватель базы данных** и нажмите кнопку " **отобразить данные таблицы**".)

2. Скопируйте в таблицу следующие данные. (Его можно скопировать, а затем вставить в таблицу, выбрав всю строку на панели результатов.)

    |**ID**|**Тип**|**FirstName**|**LastName**|**Менеджер**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Создание нового проекта
 Теперь, когда таблица создана, создайте новый проект, чтобы продемонстрировать настройку наследования.

#### <a name="to-create-the-new-windows-application"></a>Для создания нового приложения Windows

1. В меню **файл** создайте новый проект.

2. Назовите проект **инхеританцевалксраугх**.

    > [!NOTE]
    > [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] поддерживается в проектах Visual Basic и C#. Создайте новый проект на одном из этих языков.

3. Щелкните шаблон **приложения Windows Forms** и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [Client Applications](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

4. Проект Инхеританцевалксраугх создается и добавляется в **Обозреватель решений**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Добавление в проект файла LINQ to SQL Classes

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Для добавления файла LINQ to SQL в проект

1. В меню **Проект** выберите **Добавить новый элемент**.

2. Выберите шаблон **Классы LINQ to SQL** и нажмите кнопку **Добавить**.

     DBML-файл добавляется в проект, и [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] открывается.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Создание наследования с использованием реляционного конструктора объектов
 Настройте наследование путем перетаскивания объекта **Наследование** из **Панели элементов** на область конструктора.

#### <a name="to-create-the-inheritance"></a>Чтобы создать наследование, выполните следующие действия

1. В **Обозреватель сервера** / **Обозреватель базы данных**перейдите к таблице **Person** , созданной ранее.

2. Перетащите таблицу **Person** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] область конструктора.

3. Перетащите вторую таблицу **Person** на поверхность [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] и измените ее имя на **Employee**.

4. Удалите свойство **Manager** из объекта **Person**.

5. Удалите свойства **Type**, **ID**, **FirstName** и **LastName** из объекта **Employee**. (Другими словами, удалите все свойства, кроме свойства **Manager**.)

6. Из вкладки **Реляционный конструктор объектов****Панели элементов** создайте **Наследование** между объектами **Person** и **Employee**. Чтобы выполнить это, щелкните по пункту **Наследование** в **Панели элементов** и отпустите кнопку мыши. Затем щелкните объект **Employee** , а затем объект **Person** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Стрелка на линии наследования будет указывать на объект **Person** .

7. Щелкните по линии **Наследование** на области конструктора.

8. Задайте свойству **Свойство дискриминатора** значение **Type**.

9. Задайте свойству **Производное значение дискриминатора класса** значение **2**.

10. Задайте свойству **Базовое значение дискриминатора класса** значение **1**.

11. Задайте свойству **Наследование по умолчанию** значение **Person**.

12. Выполните построение проекта.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Выполнение запроса наследуемого класса и отображение данных на форме
 Теперь добавьте некоторый код в форму, которая делает запрос на определенный класс в модели объекта.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Для создания запроса LINQ и отображения результатов на форме

1. Перетащите элемент управления **ListBox** на форму Form1.

2. Дважды щелкните форму, чтобы создать обработчик событий `Form1_Load`.

3. Добавьте следующий код в обработчик событий `Form1_Load` .

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Тестирование приложения
 Запустите приложение и убедитесь, что записи, отображенные в списке представляют всех работников (записи, которые имеют значение 2 в столбце Type).

#### <a name="to-test-the-application"></a>Тестирование приложения

1. Нажмите клавишу F5.

2. Убедитесь, что отображаются только записи со значением 2 в их столбце Type.

3. Закройте форму. (В меню **Отладка** выберите команду **прерывать отладку**.)

## <a name="see-also"></a>См. также
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Практическое руководство. Добавление LINQ to SQL классов в проект (o-r Designer](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6) [) Пошаговое руководство. Создание классов LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Практическое руководство. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Практическое руководство. Создание объектной модели в Visual Basic или C#](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
