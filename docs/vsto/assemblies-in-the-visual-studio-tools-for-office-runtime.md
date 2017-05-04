---
title: "Сборки среды выполнения Visual Studio Tools for Office | Microsoft Docs"
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
  - "среда выполнения набора средств Visual Studio для Office, сборки"
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Сборки среды выполнения Visual Studio Tools for Office
  При создании проекта Office Visual Studio автоматически добавляет ссылки на сборки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], используемые для данного типа проектов и платформы .NET Framework, для которой предназначен этот проект. В расширениях Office для .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] используются разные сборки. Дополнительные сведения о расширениях Office см. в разделе [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Сборки в расширениях Office для .NET Framework 4 и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Документацию по пространствам имен и типам, включенным в эти сборки, см. в разделе [Справочные материалы по управляемому коду &#40;разработка решений Office в Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Имя сборки|Описание|  
|----------------|--------------|  
|Microsoft.Office.Tools.Common.dll|Предоставляет следующие типы:<br /><br /> -   Типы для создания настроек ленты и смарт\-тегов. **Note:**      Смарт\-теги объявлены нерекомендуемыми в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-   Типы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Excel, а также вспомогательные типы. Для получения дополнительной информации см. [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Предоставляет типы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|  
|Microsoft.Office.Tools.Word.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Word, а также вспомогательные типы. Для получения дополнительной информации см. [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Предоставляет следующие типы:<br /><br /> -   Исключения, создаваемые набором инструментов Visual Studio для среды выполнения Office.<br />-   Атрибуты, которые можно использовать при создании областей формы Outlook.|  
|Microsoft.Office.Tools.dll|Предоставляет типы, которые входят в инфраструктуру набора инструментов Visual Studio для среды выполнения Office и не предназначены для использования напрямую из кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Предоставляет следующие типы:<br /><br /> -   Атрибут <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> и интерфейс <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, которые могут использоваться для кэширования объектов данных в настройках уровня документа. Для получения дополнительной информации см. [Кэширование данных](../vsto/caching-data.md).<br />-   Интерфейс <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-   Исключения, создаваемые набором инструментов Visual Studio для среды выполнения Office.<br />-   Другие типы, являющиеся частью инфраструктуры среды выполнения набора средств Visual Studio для Office и не предназначенные для непосредственного использования из кода.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Предоставляет следующие типы:<br /><br /> -   Класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, который может использоваться для присоединения сборок настройки к документам, а также для доступа к кэшированным данным в документах. Дополнительные сведения см. в разделе [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-   Несколько классов, представляющих иерархию кэшированных данных в настройке уровня документа. Для получения дополнительной информации см. [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Проекты, предназначенные для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], также ссылаются на указанные ниже сборки. Эти сборки не входят в распространяемый пакет [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Они представляют собой независимые сборки, которые необходимо развертывать вместе с решением. По умолчанию они копируются в выходную папку построения для проекта \(свойство **Копировать локально** имеет для этих сборок значение **True**\). Если проект развертывается с помощью ClickOnce, эти сборки включаются в создаваемый пакет.  
  
|Имя сборки|Описание|  
|----------------|--------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` в проектах надстроек VSTO и создаваемого класса ленты во всех проектах.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> -   Базовые классы для создаваемых классов `ThisWorkbook` и `Sheet` в проектах уровня документа для Excel.<br />-   Элементы управления Windows Forms, которые можно использовать на листах в проектах Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` и классов области формы в проектах Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> -   Базовые классы для создаваемого класса `ThisDocument` в проектах уровня документа для Word.<br />-   Элементы управления Windows Forms, которые можно использовать в документах Word.|  
  
## Сборки в расширениях Office для .NET Framework 3.5  
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для .NET Framework 3.5. Документацию по пространствам имен и классам в этих сборках см. в следующем справочном разделе документации к Visual Studio 2008: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Имя сборки|Описание|  
|----------------|--------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Предоставляет следующие типы:<br /><br /> -   Базовый класс Microsoft.Office.Tools.AddIn для надстроек VSTO.<br />-   Классы для создания настроек ленты и смарт\-тегов. **Note:**      Смарт\-теги объявлены нерекомендуемыми в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-   Классы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Excel. Для получения дополнительной информации см. [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет классы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Word. Для получения дополнительной информации см. [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет следующие типы:<br /><br /> -   Класс Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent, предоставляющий возможности привязки данных для ведущих элементов управления в настройках на уровне документа.<br />-   Другие типы, являющиеся частью инфраструктуры среды выполнения набора средств Visual Studio для Office и не предназначенные для непосредственного использования из кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Предоставляет следующие типы:<br /><br /> -   Атрибут Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute и интерфейс Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType, которые могут использоваться для кэширования объектов данных в настройках уровня документа. Для получения дополнительной информации см. [Кэширование данных](../vsto/caching-data.md).<br />-   Исключения, создаваемые набором инструментов Visual Studio для среды выполнения Office.<br />-   Другие типы, являющиеся частью инфраструктуры среды выполнения набора средств Visual Studio для Office и не предназначенные для непосредственного использования из кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Предоставляет интерфейс Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [Развертывание расширенных решений Office](http://msdn.microsoft.com/ru-ru/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Предоставляет следующие типы:<br /><br /> -   Класс Microsoft.VisualStudio.Tools.Applications.ServerDocument, который может использоваться для программного присоединения сборок настройки к документам, а также для доступа к кэшированным данным в документах. Для получения дополнительной информации см. [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-   Несколько классов, представляющих иерархию кэшированных данных в настройке уровня документа. Для получения дополнительной информации см. [Доступ к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Предоставляет следующие типы:<br /><br /> -   Классы Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry и Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList классы, которые можно использовать для создания записей в пользовательском списке включения и предоставления доверия решениям Office, предназначенным для платформы .NET Framework 3.5.<br />-   Другие типы, являющиеся частью инфраструктуры среды выполнения набора средств Visual Studio для Office и не предназначенные для непосредственного использования из кода.|  
  
## См. также  
 [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Сценарии установки среды выполнения Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  