---
title: Основные сборки взаимодействия Office | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2ab565dfbc4fec21c646aa72b54f3694d99e6a1f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="office-primary-interop-assemblies"></a>Office - основные сборки взаимодействия
  Для использования компонентов приложения Microsoft Office из проекта Office необходимо использовать основную сборку взаимодействия (PIA) для приложения. Основная сборка взаимодействия позволяет управляемому коду взаимодействовать с основанной на COM объектной моделью приложения Microsoft Office.  
  
 При создании нового проекта Office Visual Studio добавляет ссылки на основные сборки взаимодействия, которые нужны для сборки проекта. В некоторых сценариях может потребоваться добавить ссылки на дополнительные основные сборки взаимодействия (например, если требуется использовать Microsoft Office Word в проекте для Microsoft Office Excel).  
  
 В этом разделе описываются следующие аспекты использования основных сборок взаимодействия Microsoft Office в проектах Office.  
  
-   [Разделение основных сборок взаимодействия для построения и выполнения проектов](#separateassemblies)  
  
-   [Использование компонентов нескольких приложений Microsoft Office в одном проекте](#usingfeatures)  
  
-   [Полный список основных сборок взаимодействия для приложений Microsoft Office](#pialist)  
  
 Дополнительные сведения об основных сборках взаимодействия см. в разделе [Основные сборки взаимодействия](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
##  <a name="separateassemblies"></a> Separate Primary Interop Assemblies for Building and Running Projects  
 Visual Studio использует разные наборы основных сборок взаимодействия на компьютере разработки. Эти разные наборы сборок хранятся в следующих расположениях.  
  
-   Папка в каталоге файлов программы.  
  
     Эти копии сборок используются при написании кода и построении проектов. Visual Studio устанавливает эти сборки автоматически.  
  
-   Глобальный кэш сборок.  
  
     Эти копии сборок используются в некоторых задачах разработки, например, при выполнении или отладке проектов. Visual Studio не устанавливает и не регистрирует эти сборки; это необходимо сделать вручную.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Основные сборки взаимодействия в каталоге файлов программы  
 При установке Visual Studio основные сборки взаимодействия автоматически устанавливаются в расположении в файловой системе (за пределами глобального кэша сборок). При создании нового проекта Visual Studio автоматически добавляет ссылки на эти копии основных сборок взаимодействия в ваш проект. Visual Studio использует эти копии основных сборок взаимодействия вместо сборок в глобальном кэше для разрешения ссылок при разработке и построении проекта.  
  
 Эти копии основных сборок взаимодействия помогают Visual Studio избегать различных проблем разработки, которые могут возникать при регистрации разных основных сборок взаимодействия в глобальном кэше сборок.  
  
 Visual Studio устанавливает эти копии сборок взаимодействия в следующие расположения на компьютере разработки.  
  
-   %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office14  
  
     (или %ProgramFiles(x86)%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office14 в 64-разрядных операционных системах)  
  
-   %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office15  
  
     (или %ProgramFiles(x86)%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office15 в 64-разрядных операционных системах)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Основные сборки взаимодействия в глобальном кэше сборок  
 Для выполнения определенных задач разработки основные сборки взаимодействия должны быть установлены и зарегистрированы в глобальном кэше сборок на компьютере разработки. Как правило, сборки устанавливаются автоматически при установке Office на компьютере разработки. Для получения дополнительной информации см. [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Присутствие основных сборок взаимодействия Office на компьютере конечного пользователя не требуется для запуска решений Office. Дополнительные сведения см. в разделе [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
##  <a name="usingfeatures"></a> Using Features of Multiple Microsoft Office Applications in a Single Project  
 Каждый шаблон проекта Office в Visual Studio предназначен для работы с одним приложением Microsoft Office. Чтобы использовать компоненты в нескольких приложениях Microsoft Office (или в приложении или компоненте, для которого нет проекта в Visual Studio) необходимо добавить ссылку на нужные основные сборки взаимодействия.  
  
 В большинстве случаев потребуется добавить ссылки на сборки, которые устанавливаются Visual Studio в каталоге %ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\. Эти версии сборок отображаются на вкладке **Платформа** диалогового окна **Диспетчер ссылок** . Дополнительные сведения см. в разделе [Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
 Если вы установили и зарегистрировали основные сборки взаимодействия в глобальном кэше сборок, эти версии сборок отображаются на вкладке **COM** диалогового окна **Диспетчер ссылок** . Следует избегать добавления ссылок на эти версии сборок, так как имеются несколько проблем разработки, которые могут возникать при их использовании. Например, если вы зарегистрировали разные версии основных сборок взаимодействия в глобальном кэше сборок, проект будет автоматически привязан к версии сборки, которая была зарегистрирована последней, даже если вы укажете другую версию сборки на вкладке **COM** диалогового окна **Диспетчер ссылок** .  
  
> [!NOTE]  
>  Некоторые сборки добавляются в проект автоматически при добавлении сборки, которая на них ссылается. Например, ссылки на сборки Office.dll и Microsoft.Vbe.Interop.dll добавляются автоматически при добавлении ссылки на сборки Word, Excel, Outlook, Microsoft Forms или Graph.  
  
##  <a name="pialist"></a> Основные сборки взаимодействия для приложений Microsoft Office  
 В следующей таблице перечисляются основные сборки взаимодействия, доступные для [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
|Приложение или компонент Office|Имя основной сборки взаимодействия|  
|-------------------------------------|-----------------------------------|  
|Библиотека объектов Microsoft Access 14.0<br /><br /> Библиотека объектов Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|  
|Библиотека объектов ядра СУБД Access Microsoft Office 14.0<br /><br /> Библиотека объектов ядра СУБД Access Microsoft Office 15.0|Microsoft.Office.Interop.Access.Dao.dll|  
|Библиотека объектов Microsoft Excel 14.0<br /><br /> Библиотека объектов Microsoft Excel 15.0|Microsoft.Office.Interop.Excel.dll|  
|Библиотека объектов Microsoft Graph 14.0 (используемая PowerPoint, Access и Word для графиков)<br /><br /> Библиотека объектов Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|  
|Библиотека типов Microsoft InfoPath 2.0 (только для InfoPath 2007)|Microsoft.Office.Interop.InfoPath.dll|  
|Сборка взаимодействия XML Microsoft InfoPath (только для InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Библиотека объектов Microsoft Office 14.0 (общие функции Office)<br /><br /> Библиотека объектов Microsoft Office 15.0 (общие функции Office)|office.dll|  
|Элемент управления представления Microsoft Office Outlook (может использоваться в веб-страницах и приложениях для получения доступа к папке входящих сообщений)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Библиотека объектов Microsoft Outlook 14.0<br /><br /> Библиотека объектов Microsoft Outlook 15.0|Microsoft.Office.Interop.Outlook.dll|  
|Библиотека объектов Microsoft PowerPoint 14.0<br /><br /> Библиотека объектов Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|  
|Библиотека объектов Microsoft Project 14.0<br /><br /> Библиотека объектов Microsoft Project 15.0|Microsoft.Office.Interop.MSProject.dll|  
|Библиотека объектов Microsoft Publisher 14.0<br /><br /> Библиотека объектов Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|  
|Справочная библиотека веб-объектов Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Справочная библиотека объектов страницы Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Microsoft библиотеки типов на смарт-теги 2.0 **Примечание:** смарт-теги являются устаревшими в [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] и [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Библиотека типов Microsoft Visio 14.0<br /><br /> Библиотека типов Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|  
|Библиотека типов для сохранения веб-страниц Microsoft Visio 14.0<br /><br /> Библиотека типов для сохранения веб-страниц Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Библиотека типов элементов управления рисования Microsoft Visio 14.0<br /><br /> Библиотека типов элементов управления рисования Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|  
|Библиотека объектов Microsoft Word 14.0<br /><br /> Библиотека объектов Microsoft Word 15.0|Microsoft.Office.Interop.Word.dll|  
|Microsoft Visual Basic for Applications Extensibility 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Сборки переадресации привязок  
 При установке и регистрации основных сборок взаимодействия Office в глобальном кэше сборок (вместе с Office или путем установки распространяемого пакета для основных сборок взаимодействия) сборки переадресации привязок также устанавливаются только в глобальном кэше сборок. Эти сборки позволяют гарантировать загрузку правильных версий основных сборок взаимодействия во время выполнения. Например, когда решение, которое ссылается на сборку [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] , выполняется на компьютере с версией [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] той же основной сборки взаимодействия, сборка переадресации привязки дает среде выполнения [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] указание загрузить версию [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] основной сборки взаимодействия. Дополнительные сведения см. в разделе [Практическое руководство. Включение и отключение автоматического перенаправления привязки](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Общие сведения о модели объектов Excel](../vsto/excel-object-model-overview.md)   
 [Решения InfoPath](../vsto/infopath-solutions.md)   
 [Общие сведения о модели объектов Outlook](../vsto/outlook-object-model-overview.md)   
 [Решения PowerPoint](../vsto/powerpoint-solutions.md)   
 [Решения Project](../vsto/project-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Общие справочные сведения о &#40;разработка решений Office в Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  