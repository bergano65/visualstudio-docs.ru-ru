---
title: Добавление кода для объектов TableAdapter в n-уровневых приложениях
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 75f7dd3149785520023657bb86ec8172dc379ab6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927000"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Добавление кода для объектов TableAdapter в n-уровневых приложениях
Можно расширить функциональные возможности адаптера таблицы, создав файл разделяемого класса для TableAdapter и добавления к нему кода (вместо добавления кода к *DatasetName.DataSet.Designer* файла). Разделяемые классы позволяют коду для конкретного класса необходимо распределить между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial (тип)](/dotnet/csharp/language-reference/keywords/partial-type).

Код, который определяет адаптера таблицы создается каждый раз при внесении изменений в адаптер таблицы в наборе данных. Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию адаптера таблицы. Чтобы предотвратить удаление во время повторного формирования адаптера таблицы в коде, добавьте код в файл разделяемого класса адаптера таблицы.

По умолчанию после разделения набора данных и кода адаптера таблицы, получается отдельные файлы классов в каждом проекте. Исходный проект содержит файл с именем *DatasetName.Designer.vb* (или *DatasetName.Designer.cs*), содержащий код адаптера таблицы. Проект, который определен в **проект Dataset** свойство имеет файл с именем *DatasetName.DataSet.Designer.vb* (или *DatasetName.DataSet.Designer.cs*), содержит код набора данных.

> [!NOTE]
>  При разделении наборов данных и адаптеров таблиц (посредством установки свойства **Проект DataSet**) существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.

> [!NOTE]
> Набор данных предоставляет функциональные возможности для создания <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> обработчики событий, когда требуется проверка. Дополнительные сведения см. в разделе [Добавление проверки в n уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Добавление пользовательского кода адаптера таблицы в n уровневого приложения

1.  Найдите проект, содержащий *.xsd* файл.

2.  Дважды щелкните *.xsd* файл, чтобы открыть **конструктор наборов данных**.

3.  Щелкните правой кнопкой мыши TableAdapter, который требуется добавить код, а затем выберите **Просмотр кода**.

     Разделяемый класс создается и открывается в редакторе кода.

4.  Добавьте код в объявление разделяемого класса.

5.  В следующем примере показано место добавления кода к `CustomersTableAdapter` в `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>См. также

- [Общие сведения об n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)
- [Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Создание и настройка адаптеров таблиц](create-and-configure-tableadapters.md)
- [Общие сведения об иерархическом обновлении](hierarchical-update.md)
