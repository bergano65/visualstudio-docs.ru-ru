---
title: Сохранять данные методы DBDirect адаптера таблицы | Документация Майкрософт
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cba6f91dd6dc0bb826531a312dc6ca5c94b21a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114760"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Сохранение данных с помощью методов DBDirect адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве приведены подробные инструкции для выполнения инструкций SQL непосредственно к базе данных с помощью методов DBDirect адаптера таблицы. Методы DBDirect адаптера таблицы обеспечивают точный контроль над обновлениями базы данных. Их можно использовать для выполнения определенных инструкций SQL и хранимые процедуры, вызывая отдельные `Insert`, `Update`, и `Delete` методы, необходимые для приложения (в отличие от перегруженного `Update` метод, который выполняет обновление INSERT и инструкций DELETE в одном вызове).  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
- Создайте новый **приложения Windows**.  
  
- Создание и настройка набора данных с помощью [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Выбор элемента управления, создаваемого на форме при перетаскивании элементов из окна **Источники данных**. Дополнительные сведения см. в разделе [задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
- Создание формы с привязкой к данным посредством перетаскивания элементов из окна **Источники данных** на форму.  
  
- Добавьте методы для непосредственного доступа к базе данных, выполнения операций вставки, обновления и удаления...  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
- Доступ к примеру базы данных "Борей".
  
## <a name="create-a-windows-application"></a>Создание приложения Windows  
 Первым шагом является создание **приложения Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1. В Visual Studio на **файл** меню, создайте новый **проекта**.  
  
2. Назовите проект **TableAdapterDbDirectMethodsWalkthrough**.  
  
3. Выберите **приложения Windows**, а затем выберите **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Создается проект **TableAdapterDbDirectMethodsWalkthrough**, который добавляется в **Обозреватель решений**.  
  
## <a name="create-a-data-source-from-your-database"></a>Создать источник данных из базы данных  
 В этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе таблицы `Region` в учебной базе данных "Борей". Для создания подключения необходимо иметь доступ к учебной базе данных "Борей".
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1. На **данных** меню, выберите **Показать источники данных**.  
  
2. В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.  
  
3. На **Выбор типа источника данных** выберите **базы данных**, а затем выберите **Далее**.  
  
4. На **Выбор подключения базы данных** экрана, выполните одно из следующих:  
  
    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         -или-  
  
    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.  
  
5. Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите **Далее**.  
  
6. На **сохранение подключения в файле конфигурации приложения** выберите **Далее**.  
  
7. На **Выбор объектов базы данных** экрана, разверните узел **таблиц** узла.  
  
8. Выберите `Region` таблицы, а затем выберите **Готово**.  
  
     Объект **NorthwindDataSet** добавляется в проект, и таблица `Region` отображается в окне **Источники данных**.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols в форму для отображения данных  
 Создайте элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание привязкой к данным элементы управления в форме Windows  
  
- Перетащите главный **регион** узел из **источников данных** окна в форму.  
  
     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Порядок добавления кнопок, вызывающих отдельные методы DbDirect адаптера таблицы  
  
1. Перетащите три элемента управления <xref:System.Windows.Forms.Button> из **области элементов** на **Form1** (под **RegionDataGridView**).  
  
2. Задайте следующие свойства **Имя** и **Текст** для каждой из кнопок.  
  
    |name|Текста|  
    |----------|----------|  
    |`InsertButton`|**Вставить**|  
    |`UpdateButton`|**Обновление**|  
    |`DeleteButton`|**Удалить**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Добавление кода для вставки новых записей в базу данных  
  
1. Выберите **InsertButton** создайте обработчик событий для события click и открыть форму в редакторе кода.  
  
2. Замените обработчик событий `InsertButton_Click` следующим кодом:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Добавление кода для обновления записей в базе данных  
  
1. Дважды щелкните **UpdateButton**, чтобы создать обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.  
  
2. Замените обработчик событий `UpdateButton_Click` следующим кодом:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Чтобы добавить код для удаления записей из базы данных  
  
1. Выберите **DeleteButton** создайте обработчик событий для события click и открыть форму в редакторе кода.  
  
2. Замените обработчик событий `DeleteButton_Click` следующим кодом:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
- Выберите **F5** для запуска приложения.  
  
- Выберите **вставить** и убедитесь, что новая запись отображается в сетке.  
  
- Выберите **обновления** и убедитесь, что запись обновляется в сетке.  
  
- Выберите **удалить** и убедитесь, что запись удаляется из сетки.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые может потребоваться выполнить после создания формы с привязкой к данным. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.  
  
- Добавление функциональности поиска в форму. Дополнительные сведения см. в разделе [Как Добавление параметризованного запроса в Windows Forms приложения](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
- Добавление дополнительных таблиц в набор данных посредством выбора элемента **Настроить набор данных с помощью мастера** в окне **Источники данных**. Вы можете добавить элементы управления, отображающие связанные данные, перетащив связанные узлы на форму. 
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
