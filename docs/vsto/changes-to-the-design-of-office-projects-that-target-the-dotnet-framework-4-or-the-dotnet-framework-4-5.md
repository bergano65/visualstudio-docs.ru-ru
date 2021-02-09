---
title: Проектирование изменений в проектах Office, предназначенных для платформа .NET Framework
description: Сведения об изменениях, появившихся в Visual Studio, для разработки проектов Office, предназначенных для платформа .NET Framework 4 или более поздней версии.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2bb8f6064bd2c2df55c7d0cf8fea1e25c513da0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903786"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Изменения в проектировании проектов Office, предназначенных для платформа .NET Framework 4 или платформа .NET Framework 4,5
  Начиная с версии [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], в Visual Studio появился ряд изменений в структуре проектов Office, которые ориентируются на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию. Если вы знакомы с проектами Office в предыдущих версиях Visual Studio, вам следует ознакомиться с этими изменениями до разработки проектов Office, ориентированных на платформу .NET Framework версии 4.0 или более поздней. По умолчанию, все проекты, создаваемые с помощью Visual Studio 2013 или более поздней версии, ориентируются на платформу .NET Framework 4.0 или более поздней версии.

 В следующих разделах описываются изменения в структуре проектов Office.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Общие сведения о структуре, основанной на интерфейсах среды выполнения Visual Studio 2010 Tools for Office
 При разработке проекта Office, предназначенного для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, большинство типов, используемых в среде выполнения средств Visual Studio 2010 для Office, являются интерфейсами. Это — значительное изменение по сравнению с предыдущими версиями [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], в которых эти типы являются классами. Например, при ориентировании на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию типы <xref:Microsoft.Office.Tools.Excel.Worksheet> и <xref:Microsoft.Office.Tools.Word.Document> являются интерфейсами, а не классами. Дополнительные сведения см. в статье [инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Для любых типов, экземпляры которых можно было создать непосредственно в предыдущих версиях [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], экземпляры этих типов теперь можно получить с помощью методов объекта `Globals.Factory`. Например, чтобы получить объект, реализующий интерфейс <xref:Microsoft.Office.Tools.Excel.SmartTag>, используйте метод `Globals.Factory.CreateSmartTag`. Дополнительные сведения см. в следующих разделах:

- [Обновление проектов Excel и Word, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Обновление настроек ленты в проектах Office, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Обновление областей формы в проектах Outlook, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Новые базовые классы в проектах Office
 Новая структура на основе интерфейсов среды выполнения средств Visual Studio 2010 для Office влияет на созданные классы в проектах Office, такие как `ThisDocument` , `ThisWorkbook` и `ThisAddIn` . В проектах Office, ориентированных на .NET Framework 3.5 и предыдущие версии платформы, эти созданные классы являются производными от классов в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], например, `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet` и `Microsoft.Office.Tools.AddIn`. В проектах, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, теперь эти классы [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] являются интерфейсами. Таким образом, созданные классы в проектах Office больше не могут наследовать от них свою реализацию. Вместо этого, созданные классы наследуют от новых базовых классов, например, <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>и <xref:Microsoft.Office.Tools.AddInBase>. Дополнительные сведения см. в статьях [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md) и [программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md).

 Базовые классы не являются частью распространяемого пакета [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Вместо этого, они определены в сборках служебных программ, которые входят в состав Visual Studio. Эти сборки копируются в выходную папку при сборке проектов Office и должны быть развернуты вместе с вашим решением. Дополнительные сведения о сборках служебных программ см. [в разделе сборки в инструменты Visual Studio для среды выполнения Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Критические изменения в проектах Office, которые перенацелены на платформа .NET Framework 4
 В следующей таблице перечислены наиболее важные критические изменения, которые вы можете обнаружить в проектах Office, переориентируемых на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Дополнительные сведения см. в статье [Перенос решений Office на платформа .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Критическое изменение|Последствие|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute> больше не используется и не поддерживается в проектах Office.|Этот атрибут необходимо удалить из файла кода AssemblyInfo в проектах Office, которые вы переносите из Visual Studio 2008. Дополнительные сведения см. в разделе [необходимые изменения для запуска проектов Office, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|**Удаление ExcelLocale1033Attribute** больше не используется или не поддерживается в проектах Excel.|Этот атрибут необходимо удалить из файла кода *AssemblyInfo* в проектах Excel. Дополнительные сведения см. в [статье обновление проектов Excel и Word, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Изменилась модель программирования элементов проекта **Лента (визуальный конструктор)** .|Необходимо изменить файл кода программной части для всех элементов ленты в проекте. Также необходимо изменить любой код, который создает экземпляры элементов управления ленты во время выполнения, обрабатывает события ленты или программно задает положение компонента ленты. Дополнительные сведения см. в [статье обновление настроек ленты в проектах Office, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|Изменилась модель программирования областей формы Outlook.|Необходимо изменить файл кода программной части для всех областей формы в проекте и любой код, который создает экземпляры определенных классов областей формы во время выполнения. Дополнительные сведения см. в разделе [Обновление областей формы в проектах Outlook, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Изменилась модель программирования для смарт-тегов в проектах Excel и Word. Смарт-теги объявлены нерекомендуемыми в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Если в решении используются смарт-теги, то при сборке проекта будут возникать ошибки. Так как смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], их необходимо удалить до начала тестирования и отладки решения в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] или более поздней версии.|
|Изменился синтаксис методов `GetVstoObject` и `HasVstoObject`.|Необходимо передавать объект `Globals.Factory` в эти методы, когда вы получаете к ним доступ в нативных объектах из основных сборок взаимодействия (PIA), или доступ к этим методам можно получать в объекте, который возвращается свойством `Globals.Factory` в проекте. Дополнительные сведения см. в [статье обновление проектов Excel и Word, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|События элементов управления содержимым Word связаны с новыми делегатами.|Необходимо изменить любой код, который обрабатывает события элементов управления содержимым Word, и указать новые делегаты. Дополнительные сведения см. в [статье обновление проектов Excel и Word, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Были переименованы классы `OLEObject` и `OLEControl`.|Необходимо изменить любой код, который использует экземпляры этих классов, чтобы использовать вместо них объекты <xref:Microsoft.Office.Tools.Excel.ControlSite> или <xref:Microsoft.Office.Tools.Word.ControlSite> . Дополнительные сведения см. в [статье обновление проектов Excel и Word, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Классы ведущих элементов, такие как `ThisWorkbook` , `Sheet` *n*, `ThisDocument` и `ThisAddIn` , больше не предоставляют `Dispose` метод, который можно переопределить.|Необходимо переместить любой код в переопределении метода `Dispose` в обработчик событий `Shutdown` в классе ведущего элемента, например, `ThisAddIn_Shutdown` и удалить переопределение метода `Dispose` из класса ведущего элемента.|

## <a name="see-also"></a>См. также раздел
- [Перенос решений Office на платформа .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Новые возможности разработки решений Office](/previous-versions/86bkz018(v=vs.110))
- [Общие сведения о Инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)