---
title: Сохранение данных в транзакции | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4b6d6befe4bbe29147a59b9700b8f148154e6c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562400"
---
# <a name="save-data-in-a-transaction"></a>Сохранение данных в транзакции
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сохранение данных в транзакции](https://docs.microsoft.com/visualstudio/data-tools/save-data-in-a-transaction).  
  
  
В этом пошаговом руководстве демонстрируется сохранение данных в транзакции с помощью <xref:System.Transactions> пространства имен. В данном примере используются таблицы `Customers` и `Orders` из учебной базы данных "Борей".  
  
## <a name="prerequisites"></a>Предварительные требования  
 В данном пошаговом руководстве требуется доступ к учебной базе данных "Борей". Сведения о настройке учебной базе данных Northwind, см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Создание приложения Windows  
 Первым шагом является создание **приложения Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1.  В Visual Studio на **файл** меню, создайте новый **проекта**.  
  
2.  Назовите проект **SavingDataInATransactionWalkthrough**.  
  
3.  Выберите **приложения Windows**, а затем выберите**ОК**. Дополнительные сведения см. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SavingDataInATransactionWalkthrough** проекта создается и добавляется к **обозревателе решений**.  
  
## <a name="create-a-database-data-source"></a>Создание источника данных базы данных  
 Этот шаг использует [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) для создания источника данных на основе `Customers` и `Orders` таблиц в базе данных Northwind.  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  На **данных** меню, выберите**Показать источники данных**.  
  
2.  В **источников данных** выберите **добавить новый источник данных** запустить **мастер настройки источника данных**.  
  
3.  На **Выбор типа источника данных**выберите **базы данных**, а затем выберите**Далее**.  
  
4.  На **Выбор подключения базы данных**экрана выполните одно из следующих:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         - или -  
  
    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно и создать подключение к базе данных "Борей".  
  
5.  Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите**Далее**.  
  
6.  На **сохранение подключения в файле конфигурации приложения** выберите**Далее**.  
  
7.  На **Выбор объектов базы данных** экрана, разверните узел **таблиц** узла.  
  
8.  Выберите `Customers` и `Orders` таблиц, а затем выберите**Готово**.  
  
     **NorthwindDataSet** добавляется в проект и `Customers` и `Orders` таблицы отображаются в **источников данных** окна.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols в форму  
 Созданием элементов управления с привязкой к данным путем перетаскивания элементов из **источников данных** окна на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание привязкой к данным элементы управления в форме Windows  
  
-   В **источников данных** окне разверните **клиентов** узла.  
  
-   Перетащите главный **клиентов** узел из **источников данных** окна на **Form1**.  
  
     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md),<xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
-   Перетащите связанный **заказы** узла (не главный **заказы** узла, но ниже узла связанной дочерней таблицы **факсов** столбец) на форму под  **CustomersDataGridView**.  
  
     На форме появляется <xref:System.Windows.Forms.DataGridView>. [OrdersTableAdapter](../data-tools/tableadapter-overview.md) и <xref:System.Windows.Forms.BindingSource> отображаются в области компонентов.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Добавьте ссылку на сборку System.Transactions  
 Транзакции используют пространство имен <xref:System.Transactions>. Ссылка проекта на сборку system.transactions не добавляется по умолчанию, поэтому вам нужно добавить ее вручную.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Порядок добавления ссылки на DLL-файл System.Transactions  
  
1.  На **проекта** меню, выберите**добавить ссылку**.  
  
2.  Выберите **System.Transactions**(на **.NET** вкладку), а затем выберите**ОК**.  
  
     Ссылку на **System.Transactions** добавляется в проект.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe кода в кнопке saveitem объекта BindingNavigator  
 Для первой таблицы, перетащенной на форму, код добавляется по умолчанию для `click` кнопку событий сохранения <xref:System.Windows.Forms.BindingNavigator>. Для обновления дополнительных таблиц вам необходимо добавить такой код вручную. В этом пошаговом руководстве мы выполнили рефакторинг имеющегося кода сохранения из сохранения обработчик событий нажатия кнопки. Также мы создадим несколько дополнительных методов для предоставления определенной функциональности обновления зависимости от строки должен ли быть добавлены или удалены.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>Изменение автоматически сформированного кода сохранения  
  
1.  Выберите **Сохранить** кнопку **CustomersBindingNavigator** (кнопка со значком гибкого диска).  
  
2.  Замените метод `CustomersBindingNavigatorSaveItem_Click` следующим кодом:  
  
     [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
     [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
 При согласовании изменений связанных данных применяется следующий порядок.  
  
-   Удалите дочерние записи. (В этом случае удалите записи из `Orders` таблицы.)  
  
-   Удалите родительские записи. (В этом случае удалите записи из `Customers` таблицы.)  
  
-   Вставьте родительские записи. (В данном случае вставьте записи в `Customers` таблицы.)  
  
-   Вставьте дочерние записи. (В данном случае вставьте записи в `Orders` таблицы.)  
  
#### <a name="to-delete-existing-orders"></a>Удаление существующих заказов  
  
-   Добавьте следующий `DeleteOrders` метод **Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>Удаление существующих клиентов  
  
-   Добавьте следующий `DeleteCustomers` метод **Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Добавление новых клиентов  
  
-   Добавьте следующий `AddNewCustomers` метод **Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Добавление новых заказов  
  
-   Добавьте следующий `AddNewOrders` метод **Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
-   Выберите**F5** для запуска приложения.  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

