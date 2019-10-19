---
title: Создание Windows Forms пользовательского элемента управления, поддерживающего сложную привязку данных | Документация Майкрософт
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c4a20939ed2e3a036831930749bb59b5a42315
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670054"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Создание пользовательского элемента управления Windows Forms со сложной привязкой данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При отображении данных на формах в приложениях Windows вы можете выбрать имеющиеся элементы управления в **области элементов** или создать пользовательские элементы управления, если вашему приложению требуется функциональность, отсутствующая в стандартных элементах управления. В этом пошаговом руководстве демонстрируется создание элемента управления, реализующего <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Элементы управления, реализующие <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, содержат свойство `DataSource` и `DataMember`, которое можно привязать к данным. Такие элементы управления похожи на <xref:System.Windows.Forms.DataGridView> или <xref:System.Windows.Forms.ListBox>.

 Дополнительные сведения о создании элементов управления см. в разделе [разработка Windows Forms элементов управления во время разработки](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 При создании элементов управления для использования в сценариях привязки к данным необходимо реализовать один из следующих атрибутов привязки к данным:

|Использование атрибутов привязки данных|
|-----------------------------------|
|Реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute> на простых элементах управления, таких как <xref:System.Windows.Forms.TextBox>, которые отображают отдельный столбец (или свойство) данных. Дополнительные сведения см. [в разделе создание Windows Forms пользовательского элемента управления, поддерживающего простую привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Реализуйте <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.DataGridView>, которые отображают списки (или таблицы) данных. (Этот процесс описан в данном пошаговом руководстве.)|
|Реализуйте <xref:System.ComponentModel.LookupBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.ComboBox>, которые отображают списки (или таблицы) данных, но также должны представлять отдельный столбец или отдельное свойство. Дополнительные сведения см. [в разделе создание Windows Forms пользовательского элемента управления, поддерживающего привязку данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 В этом пошаговом руководстве создается сложный элемент управления, отображающий строки данных из таблицы. В данном примере используется таблица `Customers` из учебной базы данных "Борей". Сложный элемент управления отображает таблицу клиентов в <xref:System.Windows.Forms.DataGridView> в пользовательском элементе управления.

 В этом пошаговом руководстве описаны следующие процедуры.

- Создайте новое **приложение Windows**.

- Добавление нового **пользовательского элемента управления** в проект.

- Визуальное проектирование пользовательского элемента управления.

- Реализация атрибута `ComplexBindingProperty`.

- Создайте набор данных с помощью [мастера настройки источника данных](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Задайте таблицу **Customers** в [окне Источники данных](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) , чтобы использовать новый сложный элемент управления.

- Добавьте новый элемент управления, перетащив его из **окна Источники данных** на **форму Form1**.

## <a name="prerequisites"></a>Необходимые компоненты
 Для выполнения данного пошагового руководства требуется:

- Доступ к примеру базы данных "Борей".

## <a name="create-a-windows-application"></a>Создание приложения Windows
 Первым шагом является создание **приложения Windows**.

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В Visual Studio в меню **файл** создайте новый **проект**.

2. Присвойте проекту имя **ComplexControlWalkthrough**.

3. Выберите **приложение Windows**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [Client Applications](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Создается проект **ComplexControlWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект
 Поскольку в этом пошаговом руководстве создается сложный элемент управления с возможностью привязки данных из **пользовательского элемента управления**, необходимо добавить в проект элемент **пользовательского элемента управления** .

#### <a name="to-add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект

1. В меню **Проект** выберите пункт **Добавить пользовательский элемент управления**.

2. Введите **ComplexDataGridView** в области **Имя** и нажмите кнопку **Добавить**.

     Элемент управления **ComplexDataGridView** добавляется в **Обозреватель решений** и открывается в конструкторе.

## <a name="design-the-complexdatagridview-control"></a>Разработка элемента управления ComplexDataGridView
 Этот этап добавляет <xref:System.Windows.Forms.DataGridView> в пользовательский элемент управления.

#### <a name="to-design-the-complexdatagridview-control"></a>Порядок проектирования элемента управления ComplexDataGridView

- Перетащите <xref:System.Windows.Forms.DataGridView> из **области элементов** на рабочую область конструирования пользовательского элемента управления.

## <a name="add-the-required-data-binding-attribute"></a>Добавление требуемого атрибута привязки данных
 Для сложных элементов управления, поддерживающих привязку к данным, можно реализовать <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Реализация атрибута ComplexBindingProperties

1. Переключите элемент управления **ComplexDataGridView** в представление кода. (В меню **Вид** выберите **Код**.)

2. Замените код в `ComplexDataGridView` следующим кодом:

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. В меню **Построение** выберите пункт **Построить решение**.

## <a name="creating-a-data-source-from-your-database"></a>Создание источника данных из базы данных
 В этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе таблицы `Customers` в учебной базе данных "Борей". Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения о настройке образца базы данных Northwind см. в разделе [Install SQL Server Sample databases](../data-tools/install-sql-server-sample-databases.md).

#### <a name="to-create-the-data-source"></a>Создание источника данных

1. В меню **Данные** выберите команду **Показать источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.

3. На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.

4. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.

5. Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.

6. На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. Разверните узел **Таблицы** на странице **Выбор объектов базы данных**.

8. Выберите таблицу `Customers` и нажмите кнопку **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблица `Customers` отображается в окне **Источники данных**.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Настройка таблицы Customers для использования элемента управления ComplexDataGridView
 Вы можете задать создаваемый элемент управления в окне **Источники данных** перед перетаскиванием элементов на форму.

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Порядок настройки таблицы клиентов на привязку к элементу управления ComplexDataGridView

1. Откройте **Form1** в конструкторе.

2. Разверните узел **Customers** в окне **Источники данных**.

3. Щелкните стрелку раскрывающегося списка в узле **Клиенты** и выберите **Настройка**.

4. Выберите **ComplexDataGridView** в списке **Связанные элементы управления** диалогового окна **Настройка данных интерфейса пользователя**.

5. Щелкните стрелку раскрывающегося списка в таблице `Customers` и выберите **ComplexDataGridView** в списке элементов управления.

## <a name="addcontrols-to-the-form"></a>Аддконтролс в форму
 Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Создание элементов управления с привязкой к данным на форме

- Перетащите главный узел **Customers** из окна **Источники данных** на форму. Убедитесь, что элемент управления **ComplexDataGridView** используется для вывода данных таблицы.

## <a name="running-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

- Нажмите клавишу F5 для запуска приложения.

## <a name="next-steps"></a>Следующие шаги
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после создания элемента управления, поддерживающего привязку к данным. Некоторые типичные дальнейшие действия.

- Помещение пользовательских элементов управления в библиотеку элементов управления, чтобы их можно было повторно использовать в других приложениях.

- Создание элементов управления, поддерживающих сценарии поиска. Дополнительные сведения см. [в разделе создание Windows Forms пользовательского элемента управления, поддерживающего привязку данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>См. также раздел
 [Привязка Windows Forms элементов управления к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [Настройка элемента управления для создания при перетаскивании из окна "источники данных"](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [Windows Forms элементов управления](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
