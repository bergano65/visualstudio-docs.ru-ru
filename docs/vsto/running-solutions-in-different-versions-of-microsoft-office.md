---
title: Запуска решений в различных версиях Microsoft Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 153b8faa356ceed9eecc5c616c2330f980728e49
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693972"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Запуска решений в различных версиях Microsoft Office
    
## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Запуска решений Office, созданных с помощью Visual Studio 2010 и более поздних версий  
  
|Версия Office, используемая шаблоном проекта|Целевая платформа .NET Framework проекта<sup>1</sup>|Версии Office, где можно запускать решение|Необходимая среда выполнения на компьютере конечного пользователя|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 и [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя версия|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Система Microsoft Office 2007<sup>2</sup>|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя версия|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Система Microsoft Office 2007<sup>2</sup>|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
|Система Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии<br /><br /> или<br /><br /> .NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Система Microsoft Office 2007|Набор инструментов Visual Studio 2010 для среды выполнения Office|  
  
 1. Для запуска вашего решения на компьютерах конечных пользователей должна иметься версия платформы .NET Framework, на которую ориентируется ваш проект. Например, если ваш проект ориентируется на .NET Framework 3.5, то на компьютерах конечных пользователей должна иметься именно эта платформа. В этом примере ваше решение не будет работать, если на компьютерах конечных пользователей установлена только платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
 2. В этом сценарии решение будет работать без ошибок в выпуске 2007 системы Microsoft Office только в том случае, если оно не использует функции, которые были добавлены в [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Запуска решений Office, созданных с помощью версий Visual Studio до Visual Studio 2010  
 Приложения Microsoft Office могут запускать решения, созданные с помощью версий Visual Studio до Visual Studio 2010. В некоторых случаях для этих решений требуются различные версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. На одном компьютере могут быть параллельно установлены разные версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 Следующая таблица показывает, какие версии Microsoft Office можно запустить решений, созданных с помощью предыдущих версий Visual Studio и какие версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и .NET Framework, необходимые для каждого решения.  
  
|Выпуск Visual Studio, используемый для создания решения|Версия Office, используемая шаблоном проекта|Версии Office, где можно запускать решение|Необходимая среда выполнения на компьютере конечного пользователя|Требуемая версия .NET Framework на компьютере конечного пользователя|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> или<br /><br /> Visual Studio Team System 2008|Система Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> Система Microsoft Office 2007|Visual Studio 2010 Tools для Office Runtime<sup>1</sup><br /><br /> или<br /><br /> Набор средств Visual Studio для системы Microsoft Office (версия среды выполнения: 3.0)|.NET Framework 3,5|  
|Один из следующих выпусков Visual Studio 2005 с VSTO 2005 SE<sup>2</sup> установлены:<br /><br /> — Visual Studio 2005 Tools for Office<br />— Visual Studio Team System 2005.<br />-Visual Studio 2005 Professional|Система Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (только 32-разрядная<sup>3</sup>)<br /><br /> Система Microsoft Office 2007|Среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск|.NET Framework 2.0, .NET Framework 3.0 или .NET Framework 3.5|  
|Любой из следующих выпусков Visual Studio:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />— Visual Studio 2005 Tools for Office (с или без VSTO 2005 SE<sup>2</sup> установлен)<br />-Visual Studio Team System 2005 (с или без VSTO 2005 SE<sup>2</sup> установлен)<br />— Visual Studio 2005 Professional с VSTO 2005 SE<sup>2</sup> установлен|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (только 32-разрядная<sup>3</sup>)<br /><br /> Система Microsoft Office 2007<br /><br /> Microsoft Office 2003|Среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск|.NET Framework 2.0, .NET Framework 3.0 или .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] приложения включают средства Visual Studio 2010 для Office runtime. Таким образом, эти приложения всегда используют средства Visual Studio 2010 для Office runtime, а не набора средств Visual Studio для системы Microsoft Office (версия 3.0 среды выполнения) в этом сценарии. Приложения в выпуске 2007 системы Microsoft Office могут использовать среду выполнения набора средств Visual Studio 2010 для Office или набор средств Visual Studio для системы Microsoft Office (версия среды выполнения: 3.0).  
  
 2. VSTO 2005 SE — это бесплатный дополнительный компонент для Visual Studio, который предоставляет шаблоны проекта надстроек VSTO для Microsoft Office 2003 и 2007. Его можно установить вместе с Visual Studio 2005 Professional, набором средств Visual Studio 2005 для Office или выпуском в Visual Studio Team System 2005. Дополнительные сведения см. в разделе [средств Visual Studio 2005 для Office, второй выпуск](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Решения Office, которым требуется среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск, несовместимы с 64-разрядной версией [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Для запуска этих решений в 64-разрядном выпуске [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] необходимо обновить проект до [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] или до проекта Visual Studio 2008, который ориентируется на выпуск 2007 системы Microsoft Office.  
  
## <a name="see-also"></a>См. также  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio Tools для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools для Office сценарии установки среды выполнения](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Настройка компьютера для разработки решений Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  