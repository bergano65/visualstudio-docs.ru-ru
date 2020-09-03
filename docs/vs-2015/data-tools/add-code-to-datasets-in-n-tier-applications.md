---
title: Добавление кода в наборы данных в n-уровневых приложениях | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673121"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n-уровневых приложениях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функциональные возможности набора данных можно расширить, создав файл разделяемого класса для набора данных и добавив в него код (вместо добавления кода в *DataSetName*. Файл DataSet. Designer). Разделяемые классы позволяют разделить код для определенного класса между несколькими физическими файлами. Дополнительные сведения см. в разделе [разделяемые](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) или [разделяемые классы и методы](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Код, определяющий набор данных, создается каждый раз при внесении изменений в определение набора данных. Этот код также создается при внесении изменений во время работы мастера, изменяющего конфигурацию набора данных. Чтобы предотвратить удаление кода во время повторного создания набора данных, добавьте код в файл разделяемого класса набора данных.

По умолчанию после разделения набора данных и `TableAdapter` кода результат представляет собой отдельный файл класса в каждом проекте. Исходный проект имеет файл *DataSetName*с именем. Designer. vb (или *DataSetName*. Designer.cs), который содержит `TableAdapter` код. Проект, указанный в свойстве **проекта набора данных** , имеет файл с именем *DataSetName*. DataSet. Designer. vb (или *DataSetName*. DataSet.Designer.cs). Этот файл содержит код набора данных.

> [!NOTE]
> При разделении наборов данных и `TableAdapter` s (путем установки свойства **проекта набора данных** ) существующие классы частичного набора данных в проекте не будут перемещены автоматически. Существующие разделяемые классы наборов данных необходимо вручную переместить в проект набора данных.

> [!NOTE]
> Когда необходимо добавить код проверки, конструктор наборов данных предоставляет функциональные возможности для создания <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> обработчиков событий и. Дополнительные сведения см. [в разделе Добавление проверки в n-уровневый набор данных](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n-уровневых приложениях

1. Нахождение проекта, содержащего XSD-файл (набор данных).

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

## <a name="see-also"></a>См. также раздел

- [Общие сведения о N-уровневых приложениях для работы с данными](../data-tools/n-tier-data-applications-overview.md)
- [Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [адаптеры таблиц TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Общие сведения о компоненте TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Обзор иерархического обновления](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Инструменты набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)