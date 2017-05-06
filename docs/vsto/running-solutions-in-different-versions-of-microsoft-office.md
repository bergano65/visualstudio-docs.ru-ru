---
title: "Запуск решений в различных версиях Microsoft Office"
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
  - "несколько версий Office"
  - "Office - приложения [разработка решений Office в Visual Studio], несколько версий Office"
  - "Office - разработка решений в Visual Studio, несколько версий Office"
  - "Office - решения [разработка решений Office в Visual Studio]"
  - "решения [разработка решений Office в Visual Studio], несколько версий Office"
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Запуск решений в различных версиях Microsoft Office
    
## Запуск решений Office, созданных с помощью Visual Studio 2010 и более поздних версий  
  
|Версия Office, используемая шаблоном проекта|Целевая платформа .NET Framework проекта<sup>1</sup>|Версии Office, где можно запускать решение|Необходимая среда выполнения на компьютере конечного пользователя|  
|--------------------------------------------------|----------------------------------------------------------|------------------------------------------------|-----------------------------------------------------------------------|  
|Office 2016 и [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя версия|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Выпуск 2007 системы Microsoft Office<sup>2</sup>|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя версия|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Выпуск 2007 системы Microsoft Office<sup>2</sup>|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
|Система Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии<br /><br /> или<br /><br /> .NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Система Microsoft Office 2007|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
  
 1.  Для запуска вашего решения на компьютерах конечных пользователей должна иметься версия платформы .NET Framework, на которую ориентируется ваш проект.  Например, если ваш проект ориентируется на .NET Framework 3.5, то на компьютерах конечных пользователей должна иметься именно эта платформа.  В этом примере ваше решение не будет работать, если на компьютерах конечных пользователей установлена только платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
 2.  В этом сценарии решение будет работать без ошибок в выпуске 2007 системы Microsoft Office только в том случае, если оно не использует функции, которые были добавлены в [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## Запуск решений Office, созданных с помощью версий Visual Studio до Visual Studio 2010  
 Приложения Microsoft Office могут запускать решения, созданные с помощью версий Visual Studio до Visual Studio 2010.  В некоторых случаях для этих решений требуются различные версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  На одном компьютере могут быть параллельно установлены разные версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 В следующей таблице указано, в каких версиях Microsoft Office могут работать решения, созданные с помощью предыдущих версий Visual Studio, и какие версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и .NET Framework необходимы для каждого решения.  
  
|Выпуск Visual Studio, используемый для создания решения|Версия Office, используемая шаблоном проекта|Версии Office, где можно запускать решение|Необходимая среда выполнения на компьютере конечного пользователя|Требуемая версия .NET Framework на компьютере конечного пользователя|  
|-------------------------------------------------------------|--------------------------------------------------|------------------------------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> или<br /><br /> Visual Studio Team System 2008|Система Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> Система Microsoft Office 2007|Среда выполнения набора средств Visual Studio 2010 для Office<sup>1</sup><br /><br /> или<br /><br /> Набор средств Visual Studio для системы Microsoft Office \(версия среды выполнения: 3.0\)|.NET Framework 3,5|  
|Один из следующих выпусков Visual Studio 2005 с установленной VSTO 2005 SE<sup>2</sup>:<br /><br /> -   Visual Studio 2005 Tools for Office<br />-   Visual Studio Team System 2005.<br />-   Visual Studio 2005 Professional.|Система Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] \(только 32\-разрядная<sup>3</sup>\)<br /><br /> Система Microsoft Office 2007|Среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск|.NET Framework 2.0, .NET Framework 3.0 или .NET Framework 3.5|  
|Любой из следующих выпусков Visual Studio:<br /><br /> -   Visual Studio 2008 Professional<br />-   Visual Studio Team System 2008<br />-   Набор средств Visual Studio 2005 для Office \(с установленной VSTO 2005 SE<sup>2</sup> или без нее\)<br />-   Visual Studio Team System 2005 \(с установленной VSTO 2005 SE<sup>2</sup> или без нее\)<br />-   Visual Studio 2005 Professional с установленной VSTO 2005 SE<sup>2</sup>|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] \(только 32\-разрядная<sup>3</sup>\)<br /><br /> Система Microsoft Office 2007<br /><br /> Microsoft Office 2003|Среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск|.NET Framework 2.0, .NET Framework 3.0 или .NET Framework 3.5|  
  
 1.  Приложения [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] содержат среду выполнения набора средств Visual Studio 2010 для Office. Таким образом, в этом сценарии данные приложения всегда используют среду выполнения набора средств Visual Studio 2010 для Office, а не набор средств Visual Studio для системы Microsoft Office \(версия среды выполнения: 3.0\).  Приложения в выпуске 2007 системы Microsoft Office могут использовать среду выполнения набора средств Visual Studio 2010 для Office или набор средств Visual Studio для системы Microsoft Office \(версия среды выполнения: 3.0\).  
  
 2.  VSTO 2005 SE — это бесплатный дополнительный компонент для Visual Studio, который предоставляет шаблоны проекта надстроек VSTO для Microsoft Office 2003 и 2007.  Его можно установить вместе с Visual Studio 2005 Professional, набором средств Visual Studio 2005 для Office или выпуском в Visual Studio Team System 2005.  Дополнительные сведения см. в статье [Набор средств Visual Studio 2005 для Office, второй выпуск](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3.  Решения Office, которым требуется среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск, несовместимы с 64\-разрядной версией [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  Для запуска этих решений в 64\-разрядном выпуске [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] необходимо обновить проект до [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] или до проекта Visual Studio 2008, который ориентируется на выпуск 2007 системы Microsoft Office.  
  
## См. также  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Сценарии установки среды выполнения Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Настройка компьютера для разработки решений Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  