---
title: Сохранение данных в транзакции | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671093"
---
# <a name="save-data-in-a-transaction"></a>Сохранение данных в транзакции
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как сохранить данные в транзакции с помощью пространства имен <xref:System.Transactions>. В данном примере используются таблицы `Customers` и `Orders` из учебной базы данных "Борей".

## <a name="prerequisites"></a>Необходимые компоненты
 В данном пошаговом руководстве требуется доступ к учебной базе данных "Борей".

## <a name="create-a-windows-application"></a>Создание приложения Windows
 Первым шагом является создание **приложения Windows**.

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В Visual Studio в меню **файл** создайте новый **проект**.

2. Назовите проект **савингдатаинатрансактионвалксраугх**.

3. Выберите **приложение Windows**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [Client Applications](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Создается проект **SavingDataInATransactionWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="create-a-database-data-source"></a>Создание источника данных базы данных
 На этом шаге [Мастер настройки источника данных](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) используется для создания источника данных на основе `Customers` и `Orders` таблиц в образце базы данных Northwind.

#### <a name="to-create-the-data-source"></a>Создание источника данных

1. В меню **данные** выберите команду**отобразить источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.

3. На экране **Выбор типа источника данных**выберите **база данных**, а затем нажмите кнопку **Далее**.

4. На экране **Выбор подключения к данным**выполните одно из следующих действий.

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         \- или -

    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение** и создайте подключение к базе данных "Борей".

5. Если базе данных требуется пароль, выберите параметр, чтобы включить конфиденциальные данные, а затем нажмите кнопку **Далее**.

6. На экране **сохранить строку подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. На экране **Выбор объектов базы данных** разверните узел **таблицы** .

8. Выберите таблицы `Customers` и `Orders` и нажмите кнопку **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблицы `Customers` и `Orders` отображаются в окне **Источники данных**.

## <a name="addcontrols-to-the-form"></a>Аддконтролс в форму
 Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание элементов управления с привязкой к данным в форме Windows Forms

- В окне **Источники данных** разверните узел **Клиенты** .

- Перетащите главный узел **Customers** из окна **Источники данных** на форму **Form1**.

     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.

- Перетащите связанный узел **Orders** (не главный узел **заказы** , а связанный узел дочерней таблицы ниже столбца **факса** ) в форму под элементом **кустомерсдатагридвиев**.

     На форме появляется <xref:System.Windows.Forms.DataGridView>. В области компонентов отображаются OrdersTableAdapter и <xref:System.Windows.Forms.BindingSource>.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Добавление ссылки на сборку System. Transactions
 Транзакции используют пространство имен <xref:System.Transactions>. Ссылка проекта на сборку System. Transactions не добавляется по умолчанию, поэтому ее необходимо добавить вручную.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Порядок добавления ссылки на DLL-файл System.Transactions

1. В меню **проект** выберите команду**Добавить ссылку**.

2. Выберите **System. Transactions**(на вкладке **.NET** ) и нажмите кнопку **ОК**.

     Ссылка на **System.Transactions** добавляется в проект.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Код модифисе на кнопке Савеитем BindingNavigator
 Для первой таблицы, помещенной в форму, код добавляется по умолчанию в событие `click` кнопки сохранить на <xref:System.Windows.Forms.BindingNavigator>. Для обновления дополнительных таблиц вам необходимо добавить такой код вручную. В этом пошаговом руководстве мы выполним рефакторинг существующего кода для сохранения из обработчика событий нажатия кнопки Save. Кроме того, мы создадим еще несколько методов для предоставления конкретных функций обновления в зависимости от того, нужно ли добавить или удалить строку.

#### <a name="to-modify-the-auto-generated-save-code"></a>Изменение автоматически сформированного кода сохранения

1. Нажмите кнопку **Save (сохранить** ) на **CustomersBindingNavigator** (кнопка с значком гибкого диска).

2. Замените метод `CustomersBindingNavigatorSaveItem_Click` следующим кодом:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   При согласовании изменений связанных данных применяется следующий порядок.

- Удаляет дочерние записи. (В этом случае удалите записи из таблицы `Orders`.)

- Удаление родительских записей. (В этом случае удалите записи из таблицы `Customers`.)

- Вставка родительских записей. (В этом случае вставьте записи в таблицу `Customers`.)

- Вставка дочерних записей. (В этом случае вставьте записи в таблицу `Orders`.)

#### <a name="to-delete-existing-orders"></a>Удаление существующих заказов

- Добавьте следующий метод `DeleteOrders` в **Form1**:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Удаление существующих клиентов

- Добавьте следующий метод `DeleteCustomers` в **Form1**:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Добавление новых клиентов

- Добавьте следующий метод `AddNewCustomers` в **Form1**:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Добавление новых заказов

- Добавьте следующий метод `AddNewOrders` в **Form1**:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

- Нажмите **клавишу F5** , чтобы запустить приложение.

## <a name="see-also"></a>См. также раздел
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
