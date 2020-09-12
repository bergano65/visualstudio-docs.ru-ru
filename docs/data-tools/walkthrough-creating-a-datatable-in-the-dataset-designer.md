---
title: Создание таблицы данных в конструктор наборов данных
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7dd762c6df5eebc9ebbf142a3ad7dfe430800802
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036773"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Пошаговое руководство. Создание таблицы данных в конструктор наборов данных

В этом пошаговом руководстве объясняется, как создать <xref:System.Data.DataTable> (без адаптера таблицы) с помощью **Конструктор наборов данных**. Сведения о создании таблиц данных, которые включают TableAdapter, см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Создание приложения Windows Forms

1. В Visual Studio в меню **Файл** выберите пункты **Создать** > **Проект**.

2. В левой области разверните элемент **Visual C#** или **Visual Basic** , а затем выберите пункт **Windows Desktop**.

3. В средней области выберите тип проекта **приложения Windows Forms** .

4. Назовите проект **дататаблевалксраугх**и нажмите кнопку **ОК**.

     Проект **дататаблевалксраугх** создается и добавляется в **Обозреватель решений**.

## <a name="add-a-new-dataset-to-the-application"></a>Добавление нового набора данных в приложение

1. В меню **Проект** выберите команду **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

2. На панели слева выберите **данные**, а затем выберите **набор данных** в средней области.

3. Выберите **Добавить**.

     Visual Studio добавит файл с именем **dataSet1. xsd** в проект и откроет его в **Конструктор наборов данных**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Добавить новый объект DataTable в набор данных

1. Перетащите объект **DataTable** с вкладки **набор данных** на **панели элементов** на **Конструктор наборов данных**.

     В набор данных добавляется таблица с именем **DataTable1** .

2. Щелкните строку заголовка **DataTable1** и переименуйте ее `Music` .

## <a name="add-columns-to-the-datatable"></a>Добавить столбцы в таблицу данных

1. Щелкните правой кнопкой мыши таблицу **Music** . Наведите указатель мыши на пункт **Добавить**и выберите **столбец**.

2. Присвойте столбцу имя `SongID` .

3. В окне **Свойства** присвойте свойству <xref:System.Data.DataColumn.DataType%2A> значение <xref:System.Int16?displayProperty=fullName>.

4. Повторите эту процедуру и добавьте следующие столбцы:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Задание первичного ключа для таблицы

Все таблицы данных должны иметь первичный ключ. Первичный ключ однозначно определяет определенную запись в таблице данных.

Чтобы задать первичный ключ, щелкните правой кнопкой мыши столбец **сонгид** и выберите пункт **Задать первичный ключ**. Рядом со столбцом **сонгид** появится значок ключа.

## <a name="save-your-project"></a>Сохранение проекта

Чтобы сохранить проект **дататаблевалксраугх** , в меню **файл** выберите **сохранить все**.

## <a name="see-also"></a>См. также раздел

- [Создание и настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Проверка данных](../data-tools/validate-data-in-datasets.md)
