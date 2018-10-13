---
title: 'Пошаговое руководство: Отображение связанных данных в Windows Forms | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 882c8229c105920efe247a54e9525a262e6a3246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282676"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Пошаговое руководство. Отображение связанных данных на форме в приложении Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Во многих сценариях использования приложений требуется работать с данными, поступающими из нескольких таблиц, которые часто являются связанными. Таким образом, вы хотите работать с отношением "родитель-потомок". Например, вам может потребоваться создать форму, где при выборе записи клиента отображаются заказы этого клиента. Отображение связанных записей на форме обеспечивается за счет установки свойства <xref:System.Windows.Forms.BindingSource.DataSource%2A> дочернего <xref:System.Windows.Forms.BindingSource> на родительский <xref:System.Windows.Forms.BindingSource> (не дочернюю таблицу), а также установкой для свойства <xref:System.Windows.Forms.BindingSource.DataMember%2A> дочернего <xref:System.Windows.Forms.BindingSource> отношения данных, связывающего родительскую и дочернюю таблицы между собой.  
  
 В данном пошаговом руководстве представлены следующие задачи.  
  
-   Создание **приложения Windows** проекта.  
  
-   Создание и настройка набора данных в приложении на основе `Customers` и `Orders` таблиц в базе данных "Борей" с помощью [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Добавление элементов управления для отображения данных из таблицы `Customers`.  
  
-   Добавление элементов управления для отображения `Orders` в зависимости от выбранного `Customer`.  
  
-   Тестирование приложения путем выбора различных клиентов и проверки верности отображаемых заказов для выбранного клиента.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к примеру базы данных "Борей". Для установки образцов баз данных, см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание **приложения Windows**.  
  
#### <a name="to-create-the-windows-application-project"></a>Порядок создания проекта приложения Windows  
  
1.  Из **файл** меню, создайте новый проект.  
  
2.  Задайте для проекта имя `RelatedDataWalkthrough`.  
  
3.  Выберите **приложения Windows** и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **RelatedDataWalkthrough** проекта создается и добавляется к **обозревателе решений**.  
  
## <a name="creating-the-data-source"></a>Создание источника данных  
 В этом шаге создается набор данных на основе таблиц `Customers` и `Orders` в учебной базе данных "Борей".  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  В меню **Данные** выберите команду **Показать источники данных**.  
  
2.  В **источников данных** выберите **добавить новый источник данных** запустить **мастер настройки источника данных**.  
  
3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.  
  
4.  На **Выбор подключения базы данных** странице выполните одно из следующих:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         - или -  
  
    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.  
  
5.  Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.  
  
6.  Нажмите кнопку **Далее** на **сохранение подключения в файле конфигурации приложения** страницы.  
  
7.  Разверните **таблиц** узел на **Выбор объектов базы данных** страницы.  
  
8.  Выберите **клиентов** и **заказы** таблиц, а затем щелкните **Готово**.  
  
     **NorthwindDataSet** добавляется в проект и **клиентов** таблица появится в **источников данных** окна.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Создание элементов управления для отображения данных из таблицы Customers  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Чтобы создать элементы управления для отображения данных клиентов (родительские записи):  
  
1.  В **источников данных** выберите **клиентов** таблицы, а затем щелкните стрелку раскрывающегося списка.  
  
2.  Выберите **сведения** в меню.  
  
3.  Перетащите главный **клиентов** узел из **источников данных** окна в верхней части **Form1**.  
  
     Привязанные к данным элементы управления с метками описания отображаются на форме вместе с панелью инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Создание элементов управления для отображения данных из таблицы Orders  
 ![Окно источников данных, показывающая связь](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Чтобы создать элементы управления для отображения заказов для каждого клиента (дочерних записей):  
  
-   В **источников данных** окне разверните **клиентов** узел и выберите последний столбец в **клиентов** таблицы, это разворачиваемый **заказы** узел и перетащите его на нижнюю часть **Form1**.  
  
     <xref:System.Windows.Forms.DataGridView> добавляется на форму, а новые компоненты <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) и TableAdapter (`OrdersTableAdapter`) добавляются в область компонентов.  
  
    > [!NOTE]
    >  Откройте [окно "Свойства"](../ide/reference/properties-window.md) и выберите **OrdersBindingSource**. Изучите свойства <xref:System.Windows.Forms.BindingSource.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A>, чтобы увидеть настройку привязки для отображения связанных записей. <xref:System.Windows.Forms.BindingSource.DataSource%2A> настроен на `CustomersBindingSource` (<xref:System.Windows.Forms.BindingSource> родительской таблицы), в отличие от таблицы `Orders`. Свойству <xref:System.Windows.Forms.BindingSource.DataMember%2A> присвоено значение `FK_Orders_Customers`, являющееся именем объекта <xref:System.Data.DataRelation>, связывающего таблицы друг с другом.  
  
## <a name="testing-the-application"></a>Тестирование приложения  
  
#### <a name="to-test-the-application"></a>Тестирование приложения  
  
1.  Нажмите клавишу F5 для запуска приложения.  
  
2.  Выберите различных клиентов, использующих **CustomersBindingNavigator** Чтобы проверить правильность отображения заказов в <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после создания формы с отображением вида "главный-подчиненный". Ниже приведено одно усовершенствование, которое вы можете внести в данное пошаговое руководство.  
  
-   Фильтрация записей `Customers` посредством добавления параметризации в таблицу `Customers`. Чтобы сделать это, выберите любой элемент управления, отображающий данные из `Customers` нажмите смарт-тег и выберите **добавить запрос**. Завершить [диалоговом Построитель условий поиска](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Дополнительные сведения см. в разделе [как: Добавление параметризованный запрос в приложение Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>См. также  
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Окно источников данных](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Добавление новых источников данных](../data-tools/add-new-data-sources.md)   
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Практическое: отображение связанных данных в Windows Forms приложения](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Общие сведения о компоненте BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [Общие сведения об элементе управления BindingNavigator](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)