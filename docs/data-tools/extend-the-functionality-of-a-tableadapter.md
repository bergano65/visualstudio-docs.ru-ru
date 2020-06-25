---
title: Расширение функциональных возможностей адаптера таблицы TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 245ea6791fde96c1ff08d43d138c522f43749c6b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282427"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Расширение функциональных возможностей адаптера таблицы TableAdapter

Функциональные возможности TableAdapter можно расширить, добавив код в файл разделяемого класса TableAdapter.

Код, определяющий TableAdapter, создается повторно при внесении любых изменений в TableAdapter в **Конструктор наборов данных**или когда мастер изменяет конфигурацию адаптера таблицы. Чтобы предотвратить удаление кода во время повторного создания адаптера таблицы TableAdapter, добавьте код в файл разделяемого класса TableAdapter.

Разделяемые классы позволяют разделить код для определенного класса между несколькими физическими файлами. Дополнительные сведения см. в разделе [partial](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Обнаружение адаптеров таблиц в коде

Хотя адаптеры таблиц разработаны с **Конструктор наборов данных**, созданные классы TableAdapter не являются вложенными классами <xref:System.Data.DataSet> . Адаптеры таблиц расположены в пространстве имен на основе имени связанного с TableAdapter набора данных. Например, если приложение содержит набор данных с именем `HRDataSet` , адаптеры таблиц будут находиться в `HRDataSetTableAdapters` пространстве имен. (Соглашение об именовании соответствует следующему шаблону: *DataSetName*  +  `TableAdapters` ).

В следующем примере предполагается, что TableAdapter с именем `CustomersTableAdapter` находится в проекте с `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Создание разделяемого класса для TableAdapter

1. Добавьте новый класс в проект, выбрав в меню **проект** пункт **Добавить класс**.

2. Назовите класс `CustomersTableAdapterExtended`.

3. Нажмите **Добавить**.

4. Замените код правильным пространством имен и именем разделяемого класса для проекта следующим образом:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>См. также

- [Заполнение наборов данных с помощью адаптеров таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
