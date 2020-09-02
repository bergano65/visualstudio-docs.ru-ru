---
title: Добавление кода для объектов TableAdapter в n-уровневых приложениях
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3ea451ac60de971677ee2f7910b28b334c67dff3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283103"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Добавление кода для объектов TableAdapter в n-уровневых приложениях
Вы можете расширить функциональные возможности TableAdapter, создав файл разделяемого класса для TableAdapter и добавив в него код (вместо добавления кода в файл *DataSetName. DataSet. Designer* ). Разделяемые классы позволяют разделить код для определенного класса между несколькими физическими файлами. Дополнительные сведения см. в разделе [partial](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

Код, определяющий TableAdapter, создается каждый раз при внесении изменений в TableAdapter в наборе данных. Этот код также создается при внесении изменений во время работы мастера, изменяющего конфигурацию адаптера таблицы. Чтобы предотвратить удаление кода во время повторного создания адаптера таблицы TableAdapter, добавьте код в файл разделяемого класса TableAdapter.

По умолчанию после разделения набора данных и кода TableAdapter результатом будет отдельный файл класса в каждом проекте. Исходный проект содержит файл с именем *DataSetName. Designer. vb* (или *DataSetName.Designer.CS*), который содержит код адаптера таблицы. Проект, указанный в свойстве **проекта набора данных** , имеет файл с именем *DataSetName. DataSet. Designer. vb* (или *DataSetName.DataSet.Designer.CS*), содержащий код набора данных.

> [!NOTE]
> При разделении наборов данных и адаптеров таблиц (посредством установки свойства **Проект DataSet**) существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие классы частичного набора данных необходимо вручную переместить в проект набора данных.

> [!NOTE]
> Набор данных предоставляет функциональные возможности для <xref:System.Data.DataTable.ColumnChanging> создания <xref:System.Data.DataTable.RowChanging> обработчиков событий и, когда требуется проверка. Дополнительные сведения см. [в разделе Добавление проверки в n-уровневый набор данных](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Добавление пользовательского кода в TableAdapter в n-уровневое приложение

1. Нахождение проекта, содержащего *XSD* -файл.

2. Дважды щелкните *XSD* -файл, чтобы открыть **Конструктор наборов данных**.

3. Щелкните правой кнопкой мыши TableAdapter, в который требуется добавить код, и выберите пункт **Просмотреть код**.

     Разделяемый класс создается и открывается в редакторе кода.

4. Добавьте код внутри объявления разделяемого класса.

5. В следующем примере показано, куда добавить код в в `CustomersTableAdapter` `NorthwindDataSet` :

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

## <a name="see-also"></a>См. также раздел

- [Обзор многоуровневых приложений для данных](../data-tools/n-tier-data-applications-overview.md)
- [Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Создание и настройка адаптеров таблиц](create-and-configure-tableadapters.md)
- [Общие сведения об иерархическом обновлении](hierarchical-update.md)
