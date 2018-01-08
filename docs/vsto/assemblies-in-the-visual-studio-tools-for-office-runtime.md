---
title: "Сборки в средства Visual Studio для Office Runtime | Документы Microsoft"
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
helpviewer_keywords: Visual Studio Tools for Office runtime, assemblies
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dff032c3f43c662b75f4d0b757f16e70095efc33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Сборки среды выполнения Visual Studio Tools for Office
  При создании проекта Office Visual Studio автоматически добавляет ссылки на сборки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , используемые для данного типа проектов и платформы .NET Framework, для которой предназначен этот проект. В расширениях Office для .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]используются разные сборки. Дополнительные сведения о расширениях Office см. в разделе [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Сборки в расширениях Office для .NET Framework 4 и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Документацию по пространствам имен и типы в этих сборках см. в разделе [Справочник по управляемой &#40; разработка решений Office в Visual Studio &#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Имя сборки|Описание:|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Предоставляет следующие типы:<br /><br /> -Типы для создания настроек ленты и смарт-тегов. **Примечание:** смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Типы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Excel, а также вспомогательные типы. Для получения дополнительной информации см. [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Предоставляет типы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|  
|Microsoft.Office.Tools.Word.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Word, а также вспомогательные типы. Для получения дополнительной информации см. [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Предоставляет следующие типы:<br /><br /> -Исключения, создаваемые набором средств Visual Studio для Office runtime.<br />-Атрибуты, которые можно использовать при создании Outlook области формы.|  
|Microsoft.Office.Tools.dll|Предоставляет типы, которые входят в инфраструктуру набора инструментов Visual Studio для среды выполнения Office и не предназначены для использования напрямую из кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Предоставляет следующие типы:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Атрибута и <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> интерфейс, который можно использовать для кэширования объектов данных в настройке на уровне документа. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Интерфейс, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Исключения, создаваемые набором средств Visual Studio для Office runtime.<br />— Другие типы, которые входят в состав набора средств Visual Studio для инфраструктуры среды выполнения Office и не предназначен для использования непосредственно из программного кода.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Предоставляет следующие типы:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Класс, который можно использовать для присоединения сборок настройки к документам и доступа к кэшированным данным в документах. Для получения дополнительной информации см. [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Несколько классов, представляющих иерархию кэшированных данных в настройке уровня документа. Для получения дополнительной информации см. [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Проекты, предназначенные для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , также ссылаются на указанные ниже сборки. Эти сборки не входят в распространяемый пакет [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Они представляют собой независимые сборки, которые необходимо развертывать вместе с решением. По умолчанию они копируются в выходную папку построения для проекта (свойство **Копировать локально** имеет для этих сборок значение **True**). Если проект развертывается с помощью ClickOnce, эти сборки включаются в создаваемый пакет.  
  
|Имя сборки|Описание:|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` в проектах надстроек VSTO и создаваемого класса ленты во всех проектах.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> -Базовые классы для создаваемого `ThisWorkbook` и `Sheet` классов в уровня документа проектов для Excel.<br />-Элементы управления Windows Forms, которые можно использовать на листах в проектах Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` и классов области формы в проектах Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> -Базовые классы для создаваемого `ThisDocument` классов в проектах уровня документа для Word.<br />-Элементы управления Windows Forms, которые можно использовать в документах Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Сборки в расширениях Office для .NET Framework 3.5  
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для .NET Framework 3.5. Документацию по пространствам имен и классам в этих сборках см. в следующем справочном разделе документации к Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Имя сборки|Описание:|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Предоставляет следующие типы:<br /><br /> -Microsoft.Office.Tools.AddIn базовый класс для надстроек VSTO.<br />-Классы для создания настроек ленты и смарт-тегов. **Примечание:** смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Классы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Excel. Для получения дополнительной информации см. [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет классы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Word. Для получения дополнительной информации см. [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет следующие типы:<br /><br /> -Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent класс, предоставляющий возможности привязки данных для ведущих элементов управления в настройках на уровне документа.<br />— Другие типы, которые входят в состав набора средств Visual Studio для инфраструктуры среды выполнения Office и не предназначен для использования непосредственно из программного кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Предоставляет следующие типы:<br /><br /> -Атрибут Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute и Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType интерфейс, который можно использовать для кэширования объектов данных в настройке на уровне документа. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).<br />-Исключения, создаваемые набором средств Visual Studio для Office runtime.<br />— Другие типы, которые входят в состав набора средств Visual Studio для инфраструктуры среды выполнения Office и не предназначен для использования непосредственно из программного кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Предоставляет интерфейс Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [Advanced Office Solution Deployment](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Предоставляет следующие типы:<br /><br /> -Microsoft.VisualStudio.Tools.Applications.ServerDocument класс, который можно использовать для программного присоединения сборок настройки к документам и доступа к кэшированным данным в документах. Для получения дополнительной информации см. [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Несколько классов, представляющих иерархию кэшированных данных в настройке уровня документа. Для получения дополнительной информации см. [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Предоставляет следующие типы:<br /><br /> -Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry и Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList классы, которые можно использовать для создания пользователя включения элементов списка, чтобы предоставить доверие Office решения, нацеленные на .NET Framework 3.5.<br />— Другие типы, которые входят в состав набора средств Visual Studio для инфраструктуры среды выполнения Office и не предназначен для использования непосредственно из программного кода.|  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Сценарии установки инструментов Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  