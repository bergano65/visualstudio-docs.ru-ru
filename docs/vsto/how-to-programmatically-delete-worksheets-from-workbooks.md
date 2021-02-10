---
title: Руководство. Программное удаление листов из книг
description: Сведения о программном удалении любого листа в книге Microsoft Excel с помощью ведущего элемента листа, например.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2289309932dcd1d946fc775de60a0e07892be222
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963903"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Руководство. Программное удаление листов из книг
  В книге можно удалить любой лист. Для удаления листа используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Использование ведущего элемента листа
 Если лист был добавлен в настройку на уровне документа во время разработки, для удаления указанного листа используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Следующий код удаляет лист из книги с помощью прямой ссылки на ведущий элемент листа.

> [!IMPORTANT]
> Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:
>
> - Книга Excel 2013
> - Шаблон Excel 2013
> - Книга Excel 2010
> - Шаблон Excel 2010
>
>   Если вы хотите выполнить эту задачу в любом другом типе проекта, необходимо добавить ссылку на сборку **Microsoft. Office. Interop. Excel** , а затем использовать классы из этой сборки, чтобы открыть книгу и удалить лист. Дополнительные сведения см. [в разделе руководство. Назначение приложений Office через основные сборки взаимодействия](how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Удаление листа с помощью ведущего элемента листа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> типа `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.

- Требуется удалить лист в надстройке VSTO.

- Лист, который требуется удалить, был создан во время выполнения в настройке на уровне документа.

  Следующий код удаляет лист из книги, ссылаясь на лист по номеру индекса коллекции **листов** . В этом коде предполагается, что новый лист был создан программным образом.

> [!IMPORTANT]
> Если вы хотите выполнить эту задачу в любом другом типе проекта, необходимо добавить ссылку на сборку **Microsoft. Office. Interop. Excel** , а затем использовать классы из этой сборки, чтобы открыть книгу и удалить лист. Дополнительные сведения см. [в разделе руководство. Назначение приложений Office через основные сборки взаимодействия](how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Удаление листа с помощью коллекции листов книги Excel

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](working-with-worksheets.md)
- [Как программно скрыть листы](how-to-programmatically-hide-worksheets.md)
- [Руководство. Программное перемещение листов в книгах](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Как программно выбрать листы](how-to-programmatically-select-worksheets.md)
- [Как программно добавлять новые листы в книги](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Ведущий элемент листа](worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](global-access-to-objects-in-office-projects.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](programmatic-limitations-of-host-items-and-host-controls.md)
