---
title: Свойства в проектах Office
description: Сведения о свойствах, доступных для проектов Office в Visual Studio с помощью окно свойств.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f7a2ab04e1926a53c3d3aa05023103206c6aa01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971769"
---
# <a name="properties-in-office-projects"></a>Свойства в проектах Office
  Существует несколько важных свойств, доступных для проектов Office в Visual Studio. Эти свойства доступны в окне **Свойства** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Пространство имен для ведущего элемента
 Используйте **пространство имен для свойства ведущего элемента** , чтобы изменить пространство имен для классов ведущих элементов (например, `ThisAddIn` классов, `ThisWorkbook` или `ThisDocument` ) в проектах Visual C#. Это свойство отображается в окне **Свойства** при выборе узла документа в проекте уровня документа (например, *ExcelWorkbook1.xlsx* или *WordDocument1.docx*) или в узле приложения надстройки VSTO (например, Excel или Word) в **Обозреватель решений**.

 При создании проекта Visual C# для Office ведущим элементам присваивается пространство имен на основании имени проекта. Для изменения пространства имен рекомендуется использовать свойство **Пространство имен для элемента узла** , а не изменять непосредственно файлы кода. Если вы используете это свойство, пространство имен изменяется в созданных (скрытых) файлах кода, а также в видимых файлах кода.

## <a name="cacheindocument"></a>CacheInDocument
 Свойство **CacheInDocument** появляется в окне **Свойства** для проектов на уровне документа при выборе экземпляра <xref:System.Data.DataSet> в конструкторе Visual Studio. Кэшированы могут быть только открытые члены. Убедитесь, что для свойства **Модификаторы** установлено значение **Открытый** , если вы хотите кэшировать <xref:System.Data.DataSet>.

 Это свойство принимает логическое значение:

- Выберите **true** для кэширования набора данных в документе.

- Выберите **false** , если набор данных не должен кэшироваться в документе.

  Дополнительные сведения о кэшировании данных см. [в разделе кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Значение2
 Свойство **Value2** доступно только для книги или проектов шаблонов Excel. Оно появляется в узле свойства **Привязки** в окне **Свойства** , когда вы выбираете элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в конструкторе листа.

 Используйте свойство **Value2** в окне **Свойства** , чтобы привязать свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> объекта <xref:Microsoft.Office.Tools.Excel.NamedRange> к полю в источнике данных.

## <a name="see-also"></a>См. также раздел
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
- [События в проектах Office](../vsto/events-in-office-projects.md)
