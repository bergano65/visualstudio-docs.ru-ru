---
title: Сборки в Visual Studio Tools для Office runtime
titleSuffix: ''
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a992621bc3311fa6dd9ca2703c00aa06d5998494
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838863"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Сборки в Visual Studio Tools для Office runtime
  При создании проекта Office Visual Studio автоматически добавляет ссылки на сборки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , используемые для данного типа проектов и платформы .NET Framework, для которой предназначен этот проект. В расширениях Office для .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]используются разные сборки. Дополнительные сведения о расширениях Office см. в разделе [средств Visual Studio для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Сборки в расширениях Office для .NET Framework 4 и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Документацию по пространствам имен и типам, включенным в эти сборки, см. в разделе [управляемый Справочник по &#40;разработка решений Office в Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Имя сборки|Описание:|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Предоставляет следующие типы:<br /><br /> -Типы для создания настроек ленты и смарт-тегов. **Примечание.**      Смарт-теги объявлены нерекомендуемыми в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Типы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Excel, а также вспомогательные типы. Дополнительные сведения см. в разделе [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Предоставляет типы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|  
|Microsoft.Office.Tools.Word.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Word, а также вспомогательные типы. Дополнительные сведения см. в разделе [автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Предоставляет следующие типы:<br /><br /> -Исключения, создаваемые набором средств Visual Studio для Office runtime.<br />-Атрибуты, которые можно использовать при создании Outlook областей формы.|  
|Microsoft.Office.Tools.dll|Предоставляет типы, которые входят в инфраструктуру набора инструментов Visual Studio для среды выполнения Office и не предназначены для использования напрямую из кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Предоставляет следующие типы:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Атрибут и <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> интерфейс, который можно использовать для кэширования объектов данных в настройке уровня документа. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Интерфейс, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Исключения, создаваемые набором средств Visual Studio для Office runtime.<br />-Другие типы, которые являются частью Visual Studio Tools для Office инфраструктура среды выполнения и не предназначены для использования непосредственно из программного кода.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Предоставляет следующие типы:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Класс, который можно использовать для присоединения сборок настройки к документам и доступа к кэшированным данным в документах. Дополнительные сведения см. в разделе [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Несколько классов, представляющих иерархию кэшированных данных в настройке уровня документа. Дополнительные сведения см. в разделе [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Проекты, предназначенные для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , также ссылаются на указанные ниже сборки. Эти сборки не входят в распространяемый пакет [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Они представляют собой независимые сборки, которые необходимо развертывать вместе с решением. По умолчанию они копируются в выходную папку построения для проекта (свойство **Копировать локально** имеет для этих сборок значение **True**). Если проект развертывается с помощью ClickOnce, эти сборки включаются в создаваемый пакет.  
  
|Имя сборки|Описание:|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` в проектах надстроек VSTO и создаваемого класса ленты во всех проектах.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> -Базовые классы для создаваемого `ThisWorkbook` и `Sheet` классов в документ уровня проектов для Excel.<br />-Элементы управления Windows форм, которые можно использовать на листах в проектах Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` и классов области формы в проектах Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> -Базовые классы для создаваемого `ThisDocument` классов в проектах уровня документа для Word.<br />-Элементы управления Windows форм, которые можно использовать в документах Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Сборки в расширениях Office для .NET Framework 3.5  
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для .NET Framework 3.5. Документацию по пространствам имен и классам в этих сборках, см. в следующем справочном разделе документации по Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Имя сборки|Описание:|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Предоставляет следующие типы:<br /><br /> -Microsoft.Office.Tools.AddIn базовый класс для надстроек VSTO.<br />-Классы для создания настроек ленты и смарт-тегов. **Примечание.**      Смарт-теги объявлены нерекомендуемыми в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Классы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Excel. Дополнительные сведения см. в разделе [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет классы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Word. Дополнительные сведения см. в разделе [автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет следующие типы:<br /><br /> - [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) класс, предоставляющий возможности привязки данных для элементов управления ведущего приложения в настройки уровня документа.<br />-Другие типы, которые являются частью Visual Studio Tools для Office инфраструктура среды выполнения и не предназначены для использования непосредственно из программного кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Предоставляет следующие типы:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Атрибут и <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> интерфейс, который можно использовать для кэширования объектов данных в настройке уровня документа. Дополнительные сведения см. в разделе [кэшировать данные](../vsto/caching-data.md).<br />-Исключения, создаваемые набором средств Visual Studio для Office runtime.<br />-Другие типы, которые являются частью Visual Studio Tools для Office инфраструктура среды выполнения и не предназначены для использования непосредственно из программного кода.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Предоставляет интерфейс <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [развертыванием решения Office, расширенный](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Предоставляет следующие типы:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Класс, который можно использовать для программного присоединения сборок настройки к документам и доступа к кэшированным данным в документах. Дополнительные сведения см. в разделе [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Несколько классов, представляющих иерархию кэшированных данных в настройке уровня документа. Дополнительные сведения см. в разделе [доступа к данным в документах на сервере](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Предоставляет следующие типы:<br /><br /> – Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry и Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList классы, которые можно использовать для создания пользователя включения записи списка для предоставления доверия Office решений, предназначенных для .NET Framework 3.5.<br />-Другие типы, которые являются частью Visual Studio Tools для Office инфраструктура среды выполнения и не предназначены для использования непосредственно из программного кода.|  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Tools для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools для сценарии установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
