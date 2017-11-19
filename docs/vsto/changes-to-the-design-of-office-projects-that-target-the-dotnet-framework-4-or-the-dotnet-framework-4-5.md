---
title: "Изменения проектирования проектов Office, ориентированных на .NET Framework 4 или .NET Framework 4.5 | Документы Microsoft"
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
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
ms.assetid: 290f5cb4-e2ee-4ed8-987c-2f013405cee9
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbf93e29e9bde2029bfff262a953d5858f17d084
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Изменения проектирования проектов Office, предназначенных для .NET Framework 4 или .NET Framework 4.5
  Начиная с версии [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], в Visual Studio появился ряд изменений в структуре проектов Office, которые ориентируются на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию. Если вы знакомы с проектами Office в предыдущих версиях Visual Studio, вам следует ознакомиться с этими изменениями до разработки проектов Office, ориентированных на платформу .NET Framework версии 4.0 или более поздней. По умолчанию, все проекты, создаваемые с помощью Visual Studio 2013 или более поздней версии, ориентируются на платформу .NET Framework 4.0 или более поздней версии.  
  
 В следующих разделах описываются изменения в структуре проектов Office.  
  
## <a name="understanding-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Основные сведения о структуре, основанной на интерфейсах, среды выполнения набора средств Visual Studio 2010 для Office  
 При разработке проекта Office, ориентированного на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, большинство типов, используемых в среде выполнения набора средств Visual Studio 2010 для Office, являются интерфейсами. Это — значительное изменение по сравнению с предыдущими версиями [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], в которых эти типы являются классами. Например, при ориентировании на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию типы <xref:Microsoft.Office.Tools.Excel.Worksheet> и <xref:Microsoft.Office.Tools.Word.Document> являются интерфейсами, а не классами. Для получения дополнительной информации см. [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Для любых типов, которые можно было создать непосредственно в предыдущих версиях [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], теперь используются методы объекта Globals.Factory для получения экземпляров этих типов. Например, чтобы получить объект, реализующий интерфейс <xref:Microsoft.Office.Tools.Excel.SmartTag> интерфейсом, используйте метод Globals.Factory.CreateSmartTag. Дополнительные сведения см. в следующих разделах:  
  
-   [Обновление проектов Excel и Word, переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Обновление настроек ленты в проектах Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Обновление областей формы в проектах Outlook, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Новые базовые классы в проектах Office  
 Новая структура, основанная на интерфейсах, в среде выполнения набора средств Visual Studio 2010 для Office влияет на созданные классы в проектах Office, например, `ThisDocument`, `ThisWorkbook`и `ThisAddIn`. В проектах Office, ориентированных на .NET Framework 3.5 и предыдущих версий платформы, эти созданные классы являются производными от классов в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] например Microsoft.Office.Tools.Word.Document Microsoft.Office.Tools.Excel.Worksheet, и Microsoft.Office.Tools.AddIn. В проектах, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, теперь эти классы [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] являются интерфейсами. Таким образом, созданные классы в проектах Office больше не могут наследовать от них свою реализацию. Вместо этого, созданные классы наследуют от новых базовых классов, например, <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>и <xref:Microsoft.Office.Tools.AddInBase>. Дополнительные сведения см. в разделах [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md) и [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Базовые классы не являются частью распространяемого пакета [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Вместо этого, они определены в сборках служебных программ, которые входят в состав Visual Studio. Эти сборки копируются в выходную папку при сборке проектов Office и должны быть развернуты вместе с вашим решением. Дополнительные сведения о сборках служебных программ см. в разделе [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Критические изменения в проектах Office, которые переориентируются на .NET Framework 4  
 В следующей таблице перечислены наиболее важные критические изменения, которые вы можете обнаружить в проектах Office, переориентируемых на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Дополнительные сведения см. в разделе [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Критическое изменение|Последствие|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> больше не используется и не поддерживается в проектах Office.|Этот атрибут необходимо удалить из файла кода AssemblyInfo в проектах Office, которые вы переносите из Visual Studio 2008. Дополнительные сведения см. в разделе [необходимые изменения для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|ExcelLocale1033Attribute больше не используется и не поддерживается в проектах Excel.|Этот атрибут необходимо удалить из файла кода AssemblyInfo в проектах Excel. Дополнительные сведения см. в разделе [обновление проектов Excel и Word, переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Изменилась модель программирования элементов проекта **Лента (визуальный конструктор)** .|Необходимо изменить файл кода программной части для всех элементов ленты в проекте. Также необходимо изменить любой код, который создает экземпляры элементов управления ленты во время выполнения, обрабатывает события ленты или программно задает положение компонента ленты. Дополнительные сведения см. в разделе [проекты обновление настроек ленты в Microsoft Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Изменилась модель программирования областей формы Outlook.|Необходимо изменить файл кода программной части для всех областей формы в проекте и любой код, который создает экземпляры определенных классов областей формы во время выполнения. Дополнительные сведения см. в разделе [обновление областей формы в Outlook проекты, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Изменилась модель программирования для смарт-тегов в проектах Excel и Word. Смарт-теги объявлены нерекомендуемыми в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Если в решении используются смарт-теги, то при сборке проекта будут возникать ошибки. Так как смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], их необходимо удалить до начала тестирования и отладки решения в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] или более поздней версии.|  
|Изменился синтаксис методов GetVstoObject и HasVstoObject|Необходимо передать объект Globals.Factory этих методов при доступе к ним в собственных объектах из основных сборок взаимодействия (PIA), или использовать эти методы для объекта, который возвращается свойством Globals.Factory в своем проекте. Дополнительные сведения см. в разделе [обновление проектов Excel и Word, переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|События элементов управления содержимым Word связаны с новыми делегатами.|Необходимо изменить любой код, который обрабатывает события элементов управления содержимым Word, и указать новые делегаты. Дополнительные сведения см. в разделе [обновление проектов Excel и Word, переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Классы OLEObject и OLEControl были переименованы.|Необходимо изменить любой код, который использует экземпляры этих классов, чтобы использовать вместо них объекты <xref:Microsoft.Office.Tools.Excel.ControlSite> или <xref:Microsoft.Office.Tools.Word.ControlSite> . Дополнительные сведения см. в разделе [обновление проектов Excel и Word, переносятся на платформу .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Классы ведущих элементов, таких как `ThisWorkbook`, `Sheet`  *n* , `ThisDocument`, и `ThisAddIn`, больше не предоставляют метод Dispose, который можно переопределить.|Необходимо переместить любой код в переопределение метода Dispose в обработчик событий завершения работы в классе ведущего элемента, например, `ThisAddIn_Shutdown`и удалить переопределение метода Dispose из класса ведущего элемента.|  
  
## <a name="see-also"></a>См. также  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Новые возможности разработки для Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Обзор инструментов Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  