---
title: "Свойства в проектах Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 1284d6c3-8200-4151-88ce-0b5c7765af25
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 54eb1f58c6e623df352b382df7259e4457dd4597
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="properties-in-office-projects"></a>Свойства в проектах Office
  Существует несколько важных свойств, доступных для проектов Office в Visual Studio. Эти свойства доступны в окне **Свойства** .  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>Пространство имен для элемента узла  
 Используйте свойство **Пространство имен для элемента узла** , чтобы изменить пространство имен для классов ведущих элементов (например, `ThisAddIn`, `ThisWorkbook`или `ThisDocument` ) в проектах Visual C#. Это свойство появляется в окне **Свойства** в случае выбора узла документа в проекте на уровне документа (например, ExcelWorkbook1.xlsx или WordDocument1.docx) или узла приложения в проекте надстройки VSTO (например, Excel или Word) в **обозревателе решений**.  
  
 При создании проекта Visual C# для Office ведущим элементам присваивается пространство имен на основании имени проекта. Для изменения пространства имен рекомендуется использовать свойство **Пространство имен для элемента узла** , а не изменять непосредственно файлы кода. Если вы используете это свойство, пространство имен изменяется в созданных (скрытых) файлах кода, а также в видимых файлах кода.  
  
## <a name="cacheindocument"></a>CacheInDocument  
 Свойство **CacheInDocument** появляется в окне **Свойства** для проектов на уровне документа при выборе экземпляра <xref:System.Data.DataSet> в конструкторе Visual Studio. Кэшированы могут быть только открытые члены. Убедитесь, что для свойства **Модификаторы** установлено значение **Открытый** , если вы хотите кэшировать <xref:System.Data.DataSet>.  
  
 Это свойство принимает логическое значение:  
  
-   Выберите **true** для кэширования набора данных в документе.  
  
-   Выберите **false** , если набор данных не должен кэшироваться в документе.  
  
 Дополнительные сведения о кэшировании данных см. в разделе [Cached Data in Document-Level Customizations](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="value2"></a>Value2  
 Свойство **Value2** доступно только для книги или проектов шаблонов Excel. Оно появляется в узле свойства **Привязки** в окне **Свойства** , когда вы выбираете элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в конструкторе листа.  
  
 Используйте свойство **Value2** в окне **Свойства** , чтобы привязать свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> объекта <xref:Microsoft.Office.Tools.Excel.NamedRange> к полю в источнике данных.  
  
## <a name="see-also"></a>См. также  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)   
 [События в проектах Office](../vsto/events-in-office-projects.md)  
  
  