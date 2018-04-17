---
title: 'Пошаговое руководство: Создание таблицы данных в конструкторе наборов данных | Документы Microsoft'
ms.custom: ''
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 535dc8a0cc992d83523f14f491adc5925bc1c05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Пошаговое руководство. Создание объекта DataTable с помощью конструктора наборов данных

В этом пошаговом руководстве описывается создание <xref:System.Data.DataTable> (без TableAdapter) с помощью **конструктора наборов данных**. Сведения о создании таблиц данных, использующих TableAdapter см. в разделе [создайте и настройте адаптеры таблиц TableAdapter](../data-tools/create-and-configure-tableadapters.md).  

В данном пошаговом руководстве представлены следующие задачи.  

-   Создание нового проекта приложения Windows Forms  

-   Добавление нового набора данных в приложение  

-   Добавление новой таблицы данных в набор данных  

-   Добавление столбцов в таблицу данных  

-   Задание первичного ключа для таблицы  

## <a name="creating-a-new-windows-forms-application"></a>Создание нового приложения Windows Forms

### <a name="to-create-a-new-windows-forms-application-project"></a>Создание проекта приложения Windows Forms  
  
1. В Visual Studio на **файл** последовательно выберите пункты **New**, **проекта...** .  
  
2. Разверните **Visual C#** или **Visual Basic** на левой панели, затем выберите **классического Windows**.  

3. В средней области выберите **приложение Windows Forms** тип проекта.  

4. Назовите проект **DataTableWalkthrough**, а затем выберите **ОК**. 
  
     **DataTableWalkthrough** создается проект и добавить **обозревателе решений**.  

## <a name="adding-a-new-dataset-to-the-application"></a>Добавление нового набора данных в приложение

### <a name="to-add-a-new-dataset-item-to-the-project"></a>Чтобы добавить новый элемент набора данных в проект  
  
1.  На **проекта** последовательно выберите пункты **добавить новый элемент...** .  
  
     Откроется диалоговое окно Добавление нового элемента.  
  
2.  На левой панели выберите **данные**, а затем выберите **DataSet** в средней области.  
  
3.  Выберите **Добавить**.  
  
     Visual Studio добавляет файл с именем **DataSet1.xsd** в проект и открывает его в **конструктора наборов данных**.  

## <a name="adding-a-new-datatable-to-the-dataset"></a>Добавление новой таблицы в набор данных  

### <a name="to-add-a-new-data-table-to-the-dataset"></a>Чтобы добавить новую таблицу данных в набор данных  
  
1.  Перетащите **DataTable** из **DataSet** вкладке **элементов** на **конструктора наборов данных**.  
  
     Таблица с именем **DataTable1** добавляется к набору данных.  
   
2.  Нажмите кнопку в заголовке **DataTable1** и переименуйте его в `Music`.  

## <a name="adding-columns-to-the-datatable"></a>Добавление столбцов в таблицу DataTable

### <a name="to-add-columns-to-the-datatable"></a>Для добавления столбцов в таблицу DataTable  
  
1.  Щелкните правой кнопкой мыши **Музыка** таблицы. Пункты **добавить**, а затем нажмите кнопку **столбца**.  
  
2.  Имя столбца `SongID`.  
  
3.  В **свойства** задайте <xref:System.Data.DataColumn.DataType%2A> свойства <xref:System.Int16?displayProperty=fullName>.  
  
4.  Повторите эту процедуру и добавьте следующие столбцы:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Задание первичного ключа для таблицы

Все таблицы данных должны иметь первичный ключ. Первичный ключ однозначно определяет конкретной записи в таблице данных.  
  
### <a name="to-set-the-primary-key-of-the-data-table"></a>Чтобы задать первичный ключ таблицы данных
  
-   Щелкните правой кнопкой мыши **SongID** , а затем выберите **задать первичный ключ**.  
  
     Значок ключа появится рядом с **SongID** столбца.  
  
## <a name="saving-your-project"></a>Сохранение проекта  
  
### <a name="to-save-the-datatablewalkthrough-project"></a>Чтобы сохранить проект DataTableWalkthrough  
  
-   На **файл** меню, нажмите кнопку **сохранить все**.  

## <a name="see-also"></a>См. также

[Создание и настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Проверка данных](../data-tools/validate-data-in-datasets.md)  
[Сохранение данных](../data-tools/saving-data.md)