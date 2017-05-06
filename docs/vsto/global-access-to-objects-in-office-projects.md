---
title: "Глобальный доступ к объектам в проектах Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "класс Globals, глобальный доступ к объекту"
  - "листы [разработка решений Office в Visual Studio], глобальный доступ"
  - "документы [разработка решений Office в Visual Studio], глобальный доступ"
  - "обработчики событий [разработка решений Office в Visual Studio]"
  - "ThisWorkbook_Startup"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio]"
  - "надстройки [разработка решений Office в Visual Studio], события"
  - "книги [разработка решений Office в Visual Studio], глобальный доступ"
  - "ThisWorkbook_Shutdown"
  - "настройки уровня документа [разработка решений Office в Visual Studio]"
  - "Startup - событие"
  - "Shutdown - событие"
  - "проекты [разработка решений Office в Visual Studio], глобальный доступ"
  - "документы Office [разработка решений Office в Visual Studio], глобальный доступ"
  - "ThisAddin_Startup"
  - "события [разработка решений Office в Visual Studio]"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Глобальный доступ к объектам в проектах Office
  При создании проекта Office Visual Studio автоматически создает в проекте класс с именем `Globals`. Класс `Globals` можно использовать для доступа к различным элементам проекта из любого кода проекта в среде выполнения.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Использование класса Globals  
 `Globals` является статическим классом, содержащим ссылки на определенные элементы проекта. С помощью класса `Globals` разработчик может обращаться к следующим элементам из любого кода проекта в среде выполнения:  
  
-   Классы `ThisWorkbook` и `Sheet`*n* в книге Excel или проекте шаблона. Доступ к этим объектам осуществляется с помощью свойств `Globals.ThisWorkbook` и `Sheet`*n*.  
  
-   Класс `ThisDocument` в документе Word или проекте шаблона. Доступ к этому объекту осуществляется с помощью свойства `Globals.ThisDocument`.  
  
-   Класс `ThisAddIn` в проекте надстройки VSTO. Доступ к этому объекту осуществляется с помощью свойства `Globals.ThisAddIn`.  
  
-   Все ленты проекта, настроенные с использованием конструктора лент. Доступ к лентам осуществляется с помощью свойства `Globals.Ribbons`. Для получения дополнительной информации см. [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Все области формы Outlook в проекте надстройки VSTO для Outlook. Доступ к областям формы осуществляется с помощью свойства `Globals.FormRegions`. Для получения дополнительной информации см. [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   Объект фабрики, позволяющий создавать элементы управления ленты и ведущие элементы в среде выполнения в проектах, предназначенных для платформы [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Доступ к этому объекту осуществляется с помощью свойства `Globals.Factory`. Этот объект представляет собой экземпляр класса, который реализует один из следующих интерфейсов:  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Например, свойство `Globals.Sheet1` позволяет вставлять текст в элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на листе `Sheet1`, когда пользователь нажимает кнопку на панели действий в проекте уровня документа для Excel.  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## Инициализация класса Globals  
 Код, который пытается использовать класс `Globals` до полной инициализации документа или надстройки VSTO, может вызывать исключение в среде выполнения. Например, использование класса `Globals` при объявлении переменной уровня класса может привести к сбою, потому что класс `Globals` может не инициализироваться со ссылками на все ведущие элементы перед созданием объявленного объекта.  
  
> [!NOTE]  
>  Класс `Globals` никогда не инициализируется во время разработки, но экземпляры элементов управления создаются разработчиком. Это означает, что, если создается пользовательский элемент управления, в котором свойство класса `Globals` используется в пользовательском классе элементов управления, нужно проверять, возвращает ли свойство значение **null**, прежде чем пытаться использовать возвращенный объект.  
  
## См. также  
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)   
 [Ведущий элемент книги](../vsto/workbook-host-item.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)  
  
  