---
title: Сборки в Инструменты Visual Studio среды выполнения Office
description: Сведения о том, что Visual Studio автоматически добавляет ссылки на Инструменты Visual Studio для сборок среды выполнения Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 600408231e5085009e5edc546535ca8e5110fc6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882561"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Сборки в Инструменты Visual Studio среды выполнения Office
  При создании проекта Office Visual Studio автоматически добавляет ссылки на сборки [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] , используемые для данного типа проектов и платформы .NET Framework, для которой предназначен этот проект. В расширениях Office для .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]и [!INCLUDE[net_v45](includes/net-v45-md.md)]используются разные сборки. Дополнительные сведения о расширениях Office см. в разделе [Общие сведения о инструменты Visual Studio для среды выполнения Office](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Сборки в расширениях Office для платформа .NET Framework 4 и [!INCLUDE[net_v45](includes/net-v45-md.md)]
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и [!INCLUDE[net_v45](includes/net-v45-md.md)]. Документацию по пространствам имен и типам в этих сборках см. в разделе [управляемые ссылки &#40;разработка решений Office в Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Имя сборки|Описание|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Предоставляет следующие типы:<br /><br /> — Типы для создания настроек ленты и смарт-тегов. **Примечание.**      Смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />— Типы для создания панелей действий в настройках уровня документа и настраиваемых областей задач в надстройках VSTO.|
|Microsoft.Office.Tools.Excel.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Excel, а также вспомогательные типы. Дополнительные сведения см. в разделе [Автоматизация Excel с помощью расширенных объектов](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Предоставляет типы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|
|Microsoft.Office.Tools.Word.dll|Предоставляет интерфейсы, включающие ведущие элементы и элементы управления ведущего приложения для проектов Word, а также вспомогательные типы. Дополнительные сведения см. в разделе [Автоматизация Word с помощью расширенных объектов](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Предоставляет следующие типы:<br /><br /> — Исключения, которые могут вызываться Инструменты Visual Studio для среды выполнения Office.<br />— Атрибуты, которые можно использовать при создании областей формы Outlook.|
|Microsoft.Office.Tools.dll|Предоставляет типы, которые входят в инфраструктуру набора инструментов Visual Studio для среды выполнения Office и не предназначены для использования напрямую из кода.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Предоставляет следующие типы:<br /><br /> — <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Атрибут и <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> интерфейс, которые можно использовать для кэширования объектов данных в настройке на уровне документа. Дополнительные сведения см. в разделе [кэширование данных](caching-data.md).<br />— <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Интерфейс, который можно реализовать для выполнения дополнительных шагов установки в качестве последнего шага установщика ClickOnce для решения Office. Дополнительные сведения см. в статье [развертывание решения Office с помощью ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />— Исключения, которые могут вызываться Инструменты Visual Studio для среды выполнения Office.<br />— Другие типы, которые являются частью Инструменты Visual Studio для инфраструктуры среды выполнения Office и не предназначены для использования непосредственно из кода.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Предоставляет следующие типы:<br /><br /> — <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Класс, который можно использовать для присоединения сборок настройки к документам и для доступа к кэшированным данным в документах. Дополнительные сведения см. в разделе [Управление документами на сервере с помощью класса ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />— Несколько классов, представляющих иерархию кэшированных данных в настройке на уровне документа. Дополнительные сведения см. [в разделе доступ к данным в документах на сервере](accessing-data-in-documents-on-the-server.md).|

 Проекты, предназначенные для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](includes/net-v45-md.md)] , также ссылаются на указанные ниже сборки. Эти сборки не входят в распространяемый пакет [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] . Они представляют собой независимые сборки, которые необходимо развертывать вместе с решением. По умолчанию они копируются в выходную папку построения для проекта (свойство **Копировать локально** имеет для этих сборок значение **True**). Если проект развертывается с помощью ClickOnce, эти сборки включаются в создаваемый пакет.

|Имя сборки|Описание|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` в проектах надстроек VSTO и создаваемого класса ленты во всех проектах.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> — Базовые классы для созданных `ThisWorkbook` классов и `Sheet` в проектах уровня документа для Excel.<br />— Windows Forms элементы управления, которые можно использовать на листах в проектах Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Предоставляет базовые классы для создаваемого класса `ThisAddIn` и классов области формы в проектах Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Предоставляет следующие типы:<br /><br /> — Базовые классы для созданного `ThisDocument` класса в проектах уровня документа для Word.<br />— Windows Forms элементы управления, которые можно использовать для документов в проектах Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Сборки в расширениях Office для платформа .NET Framework 3,5
 В приведенной ниже таблице перечислены сборки, включенные в расширения Office для .NET Framework 3.5. Документацию по пространствам имен и классам в этих сборках см. в следующем справочном разделе документации по Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Имя сборки|Описание|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Предоставляет следующие типы:<br /><br /> — Базовый класс Microsoft. Office. Tools. AddIn для надстроек VSTO.<br />— Классы для создания настроек ленты и смарт-тегов. **Примечание.**      Смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />— Классы для создания панелей действий в настройках уровня документа и настраиваемых панелях задач в надстройках VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Excel. Дополнительные сведения см. в разделе [Автоматизация Excel с помощью расширенных объектов](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет классы, которые можно использовать для создания пользовательских областей формы в надстройках VSTO для Outlook.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет ведущие элементы и элементы управления ведущего приложения для решений Word. Дополнительные сведения см. в разделе [Автоматизация Word с помощью расширенных объектов](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Excel.v9.0.dll|Предоставляет следующие типы:<br /><br /> — Класс [ремотебиндаблекомпонент](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) , предоставляющий возможности привязки данных для элементов управления ведущего приложения в настройках уровня документа.<br />— Другие типы, которые являются частью Инструменты Visual Studio для инфраструктуры среды выполнения Office и не предназначены для использования непосредственно из кода.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Предоставляет следующие типы:<br /><br /> — <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Атрибут и <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> интерфейс, которые можно использовать для кэширования объектов данных в настройке на уровне документа. Дополнительные сведения см. в разделе [кэширование данных](caching-data.md).<br />— Исключения, которые могут вызываться Инструменты Visual Studio для среды выполнения Office.<br />— Другие типы, которые являются частью Инструменты Visual Studio для инфраструктуры среды выполнения Office и не предназначены для использования непосредственно из кода.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Предоставляет интерфейс <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, который можно реализовать для выполнения дополнительных действий установки в качестве итогового шага установщика ClickOnce для решения Office. Дополнительные сведения см. в разделе [расширенное развертывание решений Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Предоставляет следующие типы:<br /><br /> — <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Класс, который можно использовать для программного присоединения сборок настройки к документам и для доступа к кэшированным данным в документах. Дополнительные сведения см. в разделе [Управление документами на сервере с помощью класса ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />— Несколько классов, представляющих иерархию кэшированных данных в настройке на уровне документа. Дополнительные сведения см. [в разделе доступ к данным в документах на сервере](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Предоставляет следующие типы:<br /><br /> — Классы Microsoft. VisualStudio. Tools. Office. Runtime. Security. Аддинсекуритентри и Microsoft. VisualStudio. Tools. Office. Runtime. Security. Усеринклусионлист, которые можно использовать для создания записей списка включения пользователей, чтобы предоставить доверие решениям Office, предназначенным для платформа .NET Framework 3,5.<br />— Другие типы, которые являются частью Инструменты Visual Studio для инфраструктуры среды выполнения Office и не предназначены для использования непосредственно из кода.|

## <a name="see-also"></a>См. также раздел
- [Общие сведения о Инструменты Visual Studio для среды выполнения Office](visual-studio-tools-for-office-runtime-overview.md)
- [Инструменты Visual Studio сценариев установки среды выполнения Office](visual-studio-tools-for-office-runtime-installation-scenarios.md)
