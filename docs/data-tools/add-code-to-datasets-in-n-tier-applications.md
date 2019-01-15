---
title: Добавление кода для наборов данных в n-уровневых приложениях
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c2d1784e498cb856cc388b8e7f26dd57f978e79f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927393"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n-уровневых приложениях
Можно расширить функциональные возможности набора данных путем создания файла разделяемого класса для набора данных и добавления к нему кода (вместо добавления кода к *DatasetName*. Файл Dataset.Designer). Разделяемые классы позволяют коду для конкретного класса необходимо распределить между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](/dotnet/visual-basic/language-reference/modifiers/partial) или [разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Код, который определяет набор данных создается каждый раз при внесении изменений в определение набора данных (в типизированном наборе данных). Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию набора данных. Чтобы ваш код удалилась во время повторного формирования набора данных, добавьте код в файл разделяемого класса набора данных.

По умолчанию после разделения набора данных и кода адаптера таблицы, получается отдельные файлы классов в каждом проекте. Исходный проект содержит файл с именем *DatasetName.Designer.vb* (или *DatasetName.Designer.cs*), содержащий код адаптера таблицы. Проект, который определен в **проект Dataset** свойство имеет файл с именем *DatasetName.DataSet.Designer.vb* (или *DatasetName.DataSet.Designer.cs*) . Этот файл содержит код набора данных.

> [!NOTE]
>  При разделении наборов данных и адаптеров таблиц (задавая **проект DataSet** свойство), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.

> [!NOTE]
>  При проверке кода должен быть добавлен, типизированный набор данных предоставляет функциональные возможности для создания <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> обработчики событий. Дополнительные сведения см. в разделе [Добавление проверки в n уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n уровневых приложениях

1.  Найдите проект, содержащий *.xsd* файл.

2.  Выберите **.xsd** файл, чтобы открыть набор данных.

3.  Щелкните правой кнопкой мыши таблицу данных, к которому требуется добавить код (имя таблицы в строке заголовка), а затем выберите **Просмотр кода**.

     Разделяемый класс создается и открывается в редакторе кода.

4.  Добавьте код в объявление разделяемого класса.

     В следующем примере показано место добавления кода к CustomersDataTable в NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```
    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>См. также

- [Общие сведения об n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)
- [Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Создание и настройка адаптеров таблиц](create-and-configure-tableadapters.md)
- [Общие сведения об иерархическом обновлении](hierarchical-update.md)
- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)