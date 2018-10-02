---
title: 'Пошаговое руководство: Создание таблицы данных в конструкторе наборов данных | Документация Майкрософт'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 832dba200fca438d000bae101381389ea20cfb17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561062"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Пошаговое руководство. Создание объекта DataTable с помощью конструктора наборов данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве описывается создание <xref:System.Data.DataTable> (без TableAdapter) с помощью **конструктор наборов данных**. Сведения о создании таблиц данных, использующих адаптеры таблиц, см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).  
  
 В данном пошаговом руководстве представлены следующие задачи.  
  
-   Создание нового проекта приложения Windows  
  
-   Добавление нового набора данных в приложение  
  
-   Добавление новой таблицы данных в набор данных  
  
-   Добавление столбцов в таблице данных  
  
-   Задание первичного ключа для таблицы  
  
## <a name="creating-a-new-windows-application"></a>Создание нового приложения Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Порядок создания нового проекта приложения Windows  
  
1.  Из **файл** меню, создайте новый проект.  
  
2.  Выберите язык программирования в **типы проектов** области.  
  
3.  Нажмите кнопку **приложения Windows** в **шаблоны** области.  
  
4.  Назовите проект `DataTableWalkthrough`, а затем нажмите кнопку **ОК**.  
  
     Visual Studio добавит проект в **обозревателе решений** и отображает **Form1** в конструкторе.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Добавление нового набора данных в приложение  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Добавление нового элемента набора данных в проект  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
     Откроется диалоговое окно добавления нового элемента.  
  
2.  В **шаблоны** выберите **набора данных**.  
  
3.  Нажмите кнопку **Добавить**.  
  
     Visual Studio добавит в файл с именем **DataSet1.xsd** в проект и откройте его в **конструктор наборов данных**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Добавление новой таблицы к набору данных  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Чтобы добавить новую таблицу данных к набору данных  
  
1.  Перетащите **DataTable** из **набора данных** вкладке **элементов** на **конструктор наборов данных**.  
  
     Таблица с именем **DataTable1** добавляется к набору данных.  
  
    > [!NOTE]
    >  Чтобы создать таблицу данных, содержащую TableAdapter, см. в разделе [Пошаговое руководство: Создание адаптера таблицы с несколькими запросами](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Щелкните заголовок **DataTable1** и переименуйте его `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Добавление столбцов в таблице данных  
  
#### <a name="to-add-columns-to-the-data-table"></a>Для добавления столбцов к таблице данных  
  
1.  Щелкните правой кнопкой мыши **музыки** таблицы. Пункты **добавить**, а затем нажмите кнопку **столбец**.  
  
2.  Присвойте столбцу имя `SongID`.  
  
3.  В **свойства** окне <xref:System.Data.DataColumn.DataType%2A> свойства <xref:System.Int16?displayProperty=fullName>.  
  
4.  Повторите эту процедуру и добавьте следующие столбцы:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Задание первичного ключа для таблицы  
 Все таблицы данных должна иметь первичный ключ. Первичный ключ однозначно определяет определенной записи в таблице данных.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Чтобы задать первичный ключ таблицы данных  
  
-   Щелкните правой кнопкой мыши **SongID** столбец, а затем щелкните **задать первичный ключ**.  
  
     Рядом с полем отображается значок ключа **SongID** столбца.  
  
## <a name="saving-your-project"></a>Сохранение проекта  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Чтобы сохранить проект DataTableWalkthrough  
  
-   На **файл** меню, щелкните **сохранить все**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Теперь, когда таблица создана, может потребоваться выполнить одно из следующих действий:  
  
|Кому|См.|  
|--------|---------|  
|Создание формы для ввода данных.|[Пошаговое руководство: Отображение данных в форме Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Добавление данных в таблицу|[Добавление данных в таблицу данных](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Просмотр данных в таблицу|[Просмотр данных в объект DataTable](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Изменение данных|[Редактирование DataTable](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Удалить строку из таблицы|[Удаление DataRow](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>См. также  
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)