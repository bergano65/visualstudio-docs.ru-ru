---
title: Добавление кода для наборов данных в n-уровневых приложениях
description: Добавление кода в наборы данных в n-уровневых приложениях в Visual Studio. Создайте файл разделяемого класса для набора данных и добавьте в него код (вместо DatasetName. DataSet. Designer).
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bdbd6e728ebd4adea1a18d842651e9941098249c
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382199"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n-уровневых приложениях

Функциональные возможности набора данных можно расширить, создав файл разделяемого класса для набора данных и добавив в него код (вместо добавления кода в *DataSetName*. Файл DataSet. Designer). Разделяемые классы позволяют разделить код для определенного класса между несколькими физическими файлами. Дополнительные сведения см. в разделе [разделяемые](/dotnet/visual-basic/language-reference/modifiers/partial) или [разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Код, определяющий набор данных, создается каждый раз при внесении изменений в определение набора данных (в типизированном наборе данных). Этот код также создается при внесении изменений во время работы мастера, изменяющего конфигурацию набора данных. Чтобы предотвратить удаление кода во время повторного создания набора данных, добавьте код в файл разделяемого класса набора данных.

По умолчанию после разделения набора данных и кода TableAdapter результатом будет отдельный файл класса в каждом проекте. Исходный проект содержит файл с именем *DataSetName. Designer. vb* (или *DataSetName.Designer.CS* ), который содержит код адаптера таблицы. Проект, указанный в свойстве **проекта набора данных** , имеет файл с именем *DataSetName. DataSet. Designer. vb* (или *DataSetName.DataSet.Designer.CS* ). Этот файл содержит код набора данных.

> [!NOTE]
> При разделении наборов данных и адаптеров таблиц (с помощью свойства **Project DataSet** ) существующие классы частичного набора данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных необходимо вручную переместить в проект набора данных.

> [!NOTE]
> При необходимости добавления кода проверки типизированный набор данных предоставляет функциональные возможности для создания <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> обработчиков событий и. Дополнительные сведения см. [в разделе Добавление проверки в n-уровневый набор данных](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Добавление кода в наборы данных в n-уровневых приложениях

1. Нахождение проекта, содержащего *XSD* -файл.

2. Выберите **XSD** -файл, чтобы открыть набор данных.

3. Щелкните правой кнопкой мыши таблицу данных, в которую нужно добавить код (имя таблицы в заголовке окна), и выберите пункт **Просмотреть код**.

     Разделяемый класс создается и открывается в редакторе кода.

4. Добавьте код внутри объявления разделяемого класса.

     В следующем примере показано, куда добавить код в Кустомерсдататабле в NorthwindDataSet:

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

- [Обзор многоуровневых приложений для данных](../data-tools/n-tier-data-applications-overview.md)
- [Добавление кода для объектов TableAdapter в n-уровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Создание и настройка адаптеров таблиц TableAdapter](create-and-configure-tableadapters.md)
- [Общие сведения об иерархическом обновлении](hierarchical-update.md)
- [Инструменты набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
