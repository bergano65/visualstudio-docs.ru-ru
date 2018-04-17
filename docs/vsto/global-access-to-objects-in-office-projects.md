---
title: Глобальный доступ к объектам в проектах Office | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fda3dee12cdea7442d0f92a2ba794551d76b14cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="global-access-to-objects-in-office-projects"></a>Глобальный доступ к объектам в проектах Office
  При создании проекта Office Visual Studio автоматически создает в проекте класс с именем `Globals` . Класс `Globals` можно использовать для доступа к различным элементам проекта из любого кода проекта в среде выполнения.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Использование класса Globals  
 `Globals` является статическим классом, содержащим ссылки на определенные элементы проекта. С помощью класса `Globals` разработчик может обращаться к следующим элементам из любого кода проекта в среде выполнения:  
  
-   Классы `ThisWorkbook` и `Sheet`*n* в книге Excel или проекте шаблона. Доступ к этим объектам осуществляется с помощью свойств `Globals.ThisWorkbook` и `Sheet`*n* .  
  
-   Класс `ThisDocument` в документе Word или проекте шаблона. Доступ к этому объекту осуществляется с помощью свойства `Globals.ThisDocument` .  
  
-   Класс `ThisAddIn` в проекте надстройки VSTO. Доступ к этому объекту осуществляется с помощью свойства `Globals.ThisAddIn` .  
  
-   Все ленты проекта, настроенные с использованием конструктора лент. Доступ к лентам осуществляется с помощью свойства `Globals.Ribbons` . Для получения дополнительной информации см. [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Все области формы Outlook в проекте надстройки VSTO для Outlook. Доступ к областям формы осуществляется с помощью свойства `Globals.FormRegions` . Для получения дополнительной информации см. [Accessing a Form Region at Run Time](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   Объект фабрики, позволяющий создавать элементы управления ленты и ведущие элементы в среде выполнения в проектах, предназначенных для платформы [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Доступ к этому объекту осуществляется с помощью свойства `Globals.Factory` . Этот объект представляет собой экземпляр класса, который реализует один из следующих интерфейсов:  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Например, свойство `Globals.Sheet1` позволяет вставлять текст в элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на листе `Sheet1` , когда пользователь нажимает кнопку на панели действий в проекте уровня документа для Excel.  
  
 [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
 [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initializing-the-globals-class"></a>Инициализация класса Globals  
 Код, который пытается использовать класс `Globals` до полной инициализации документа или надстройки VSTO, может вызывать исключение в среде выполнения. Например, использование класса `Globals` при объявлении переменной уровня класса может привести к сбою, потому что класс `Globals` может не инициализироваться со ссылками на все ведущие элементы перед созданием объявленного объекта.  
  
> [!NOTE]  
>  Класс `Globals` никогда не инициализируется во время разработки, но экземпляры элементов управления создаются разработчиком. Это означает, что, если создается пользовательский элемент управления, в котором свойство класса `Globals` используется в пользовательском классе элементов управления, нужно проверять, возвращает ли свойство значение **null** , прежде чем пытаться использовать возвращенный объект.  
  
## <a name="see-also"></a>См. также  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)   
 [Ведущий элемент книги](../vsto/workbook-host-item.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  