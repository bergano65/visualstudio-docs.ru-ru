---
title: 'Пошаговое руководство: Создание набора данных с помощью конструктора наборов данных | Документация Майкрософт'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d77d63cc82b7af6281183b3eae67d09b0454fffb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868265"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Пошаговое руководство. Создание набора данных с помощью конструктора наборов данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы создадите набор данных с помощью **конструктор наборов данных**. Он поможет выполнить процесс создания проекта и добавления нового **набора данных** элемента к нему. Вы узнаете о создании таблиц, основанных на таблицах в базе данных без использования мастера.  
  
 В данном пошаговом руководстве представлены следующие задачи.  
  
- Создание нового **приложения Windows** проекта.  
  
- Добавление пустой **набора данных** элемента в проект.  
  
- Создание и настройка источника данных в приложении путем создания набора данных с помощью **конструктор наборов данных**.  
  
- Создание подключения к базе данных Northwind в **обозревателя серверов**.  
  
- Создание таблиц с помощью адаптеров таблиц в наборе данных, основанных на таблицах в базе данных.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к учебной базе данных "Борей" (версия SQL Server или Access). Дополнительные сведения см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Создание нового проекта приложения Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Порядок создания нового проекта приложения Windows  
  
1.  Из **файл** меню, создайте новый проект.  
  
2.  Выберите язык программирования в **типы проектов** области.  
  
3.  Нажмите кнопку **приложения Windows** в **шаблоны** области.  
  
4.  Назовите проект `DatasetDesignerWalkthrough`, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] добавит проект, чтобы **обозревателе решений** и отобразить новую форму в конструкторе.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Добавление нового набора данных в приложение  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Добавление нового элемента набора данных в проект  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
2.  В **шаблоны** поле **Добавление нового элемента** диалоговом окне щелкните **набора данных**.  
  
3.  Имя набора данных `NorthwindDataset`, а затем нажмите кнопку **добавить**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] будет добавлен файл с именем **NorthwindDataset.xsd** в проект и откройте его в **конструктор наборов данных**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Создание подключения к данным в обозревателе серверов  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Чтобы создать подключение к базе данных "Борей"  
  
1.  На **представление** меню, щелкните **обозревателя серверов**.  
  
2.  В **обозревателя серверов**, нажмите кнопку **подключение к базе данных** кнопки.  
  
3.  Создайте подключение к базе данных Northwind.  
  
    > [!NOTE]
    >  Можно подключиться к SQL Server или Access версии "Борей" в этом пошаговом руководстве.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Создание таблиц в наборе данных  
 В этом разделе объясняется, как добавление таблиц в наборе данных.  
  
#### <a name="to-create-the-customers-table"></a>Чтобы создать таблицу Customers  
  
1.  Разверните узел соединения данных, созданную в **обозревателя серверов**и затем разверните **таблиц** узла.  
  
2.  Перетащите **клиентов** таблицу **обозревателя серверов** на **конструктор наборов данных**.  
  
     Объект **клиентов** таблицы данных и **CustomersTableAdapter** добавляются в набор данных.  
  
#### <a name="to-create-the-orders-table"></a>Чтобы создать таблицу Orders  
  
-   Перетащите **заказы** таблицу **обозревателя серверов** на **конструктор наборов данных**.  
  
     **Заказы** таблицы данных, **OrdersTableAdapter**и связь между данными **клиентов** и **заказы** таблицы добавляются набор данных.  
  
#### <a name="to-create-the-orderdetails-table"></a>Чтобы создать таблицу OrderDetails  
  
-   Перетащите **Order Details** таблицу **обозревателя серверов** на **конструктор наборов данных**.  
  
     **Order Details** таблицы данных, **DetailsTableAdapter порядок**и связь между данными **заказы** и **Order Details** таблиц добавляются в набор данных.  
  
## <a name="next-steps"></a>Следующие шаги  
  
### <a name="to-add-functionality-to-your-application"></a>Добавление функциональности в приложение  
  
-   Сохраните набор данных.  
  
-   Выберите элементы из **источников данных** окно и перетащите их на форму. Дополнительные сведения см. в разделе [управляет привязки Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Добавьте дополнительные запросы для объектов TableAdapter. Дополнительные сведения см. в разделе [как: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Добавьте логику проверки <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> событий таблиц данных в наборе данных. Дополнительные сведения см. в разделе [проверки данных в наборах данных](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>См. также  
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)