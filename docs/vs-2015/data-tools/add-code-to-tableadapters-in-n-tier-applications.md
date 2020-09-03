---
title: Добавление в n-уровневые приложения кода для адаптеров таблиц | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673101"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Добавление кода для объектов TableAdapter в n-уровневых приложениях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете расширить функциональные возможности `TableAdapter` , создав частичный файл класса для `TableAdapter` и добавив в него код (вместо добавления кода в *DataSetName*. Файл DataSet. Designer). Разделяемые классы позволяют разделить код для определенного класса между несколькими физическими файлами. Дополнительные сведения см. в разделе [partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) или [partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 Код, определяющий, `TableAdapter` создается каждый раз при внесении изменений в `TableAdapter` . Этот код также создается при внесении изменений во время работы мастера, изменяющего конфигурацию `TableAdapter` . Чтобы предотвратить удаление кода во время повторного создания `TableAdapter` , добавьте код в файл разделяемого класса объекта `TableAdapter` .

 По умолчанию после разделения набора данных и `TableAdapter` кода результат представляет собой отдельный файл класса в каждом проекте. Исходный проект имеет файл с именем *DataSetName*. Designer. vb (или *DataSetName*. Designer.cs), который содержит `TableAdapter` код. Проект, указанный в свойстве **проекта набора данных** , имеет файл с именем *DataSetName*. DataSet. Designer. vb (или *DataSetName*. DataSet.Designer.cs), который содержит код набора данных.

> [!NOTE]
> При разделении наборов данных и `TableAdapter` s (путем установки свойства **проекта набора данных** ) существующие классы частичного набора данных в проекте не будут перемещены автоматически. Существующие разделяемые классы наборов данных необходимо вручную переместить в проект набора данных.

> [!NOTE]
> Конструктор наборов данных предоставляет функциональные возможности для <xref:System.Data.DataTable.ColumnChanging> создания <xref:System.Data.DataTable.RowChanging> обработчиков событий и, когда требуется проверка. Дополнительные сведения см. [в разделе Добавление проверки в n-уровневый набор данных](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Добавление пользовательского кода в TableAdapter в n-уровневое приложение

1. Нахождение проекта, содержащего XSD-файл (набор данных).

2. Дважды щелкните **XSD** -файл, чтобы открыть набор данных.

3. Щелкните правой кнопкой мыши объект, `TableAdapter` в который требуется добавить код, и выберите команду**Просмотреть код**.

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

## <a name="see-also"></a>См. также:
 [Общие сведения о n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md) [для обработки данных добавление кода в наборы DataSet в N-уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [адаптеры таблиц TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [Обзор](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) [иерархического обновления](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)