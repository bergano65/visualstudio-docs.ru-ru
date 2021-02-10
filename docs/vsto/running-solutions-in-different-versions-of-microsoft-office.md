---
title: Запуск решений в разных версиях Microsoft Office
description: Узнайте, как можно запускать версии Microsoft Office решений, созданных с помощью Visual Studio 2010 и более поздних версий.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f9083a92482a99d7ec7ecce144ece2806e9889e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961395"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Запуск решений в разных версиях Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Запуск решений Office, созданных с помощью Visual Studio 2010 и более поздних версий

|Версия Office, используемая шаблоном проекта|Целевой платформа .NET Framework проекта<sup>1</sup>|Версии Office, где можно запускать решение|Требуемая среда выполнения на компьютере конечного пользователя|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 и [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office система<sup>2</sup>|Среда выполнения Visual Studio 2010 Tools для Office|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office система<sup>2</sup>|Среда выполнения Visual Studio 2010 Tools для Office|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Среда выполнения Visual Studio 2010 Tools для Office|
|Система Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии<br /><br /> или диспетчер конфигурации служб<br /><br /> .NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Система Microsoft Office 2007|Среда выполнения Visual Studio 2010 Tools для Office|

 1. Для запуска решения на компьютерах конечных пользователей требуется версия платформа .NET Framework, для которой предназначен проект. Например, если проект предназначен для платформа .NET Framework 3,5, на компьютерах конечных пользователей требуется платформа .NET Framework 3,5. В этом примере решение не будет выполняться, если [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] на компьютерах конечных пользователей установлено только приложение.

 2. В этом сценарии решение будет работать без ошибок в выпуске 2007 системы Microsoft Office только в том случае, если оно не использует возможности, которые были добавлены в [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Запуск решений Office, созданных с помощью версий Visual Studio до Visual Studio 2010
 Приложения Microsoft Office могут запускать решения, созданные с помощью версий Visual Studio до Visual Studio 2010. В некоторых случаях для этих решений требуются различные версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Разные версии служб [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] можно установить параллельно на одном компьютере.

 В следующей таблице показано, какие версии Microsoft Office могут выполнять решения, созданные с помощью предыдущих версий Visual Studio, и какие версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и платформа .NET Framework необходимы для каждого решения.

|Выпуск Visual Studio, используемый для создания решения|Версия Office, используемая шаблоном проекта|Версии Office, где можно запускать решение|Требуемая среда выполнения на компьютере конечного пользователя|Требуемая версия платформа .NET Framework на компьютере конечного пользователя|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> или диспетчер конфигурации служб<br /><br /> Visual Studio Team System 2008|Система Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> Система Microsoft Office 2007|Visual Studio 2010 Tools для Office Runtime<sup>1</sup><br /><br /> или диспетчер конфигурации служб<br /><br /> Набор средств Visual Studio для системы Microsoft Office (версия среды выполнения: 3.0)|.NET Framework 3,5|
|Один из следующих выпусков Visual Studio 2005 с VSTO 2005 SE<sup>2</sup> установлен:<br /><br /> — Visual Studio 2005 Tools for Office<br />— Visual Studio Team System 2005<br />— Visual Studio 2005 Professional|Система Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-разрядное только<sup>3</sup>)<br /><br /> Система Microsoft Office 2007|Среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск|.NET Framework 2.0, .NET Framework 3.0 или .NET Framework 3.5|
|Любой из следующих выпусков Visual Studio:<br /><br /> — Visual Studio 2008 Professional<br />— Visual Studio Team System 2008<br />— Visual Studio 2005 Tools для Office (с установленным или без VSTO 2005 SE<sup>2</sup> )<br />— Visual Studio Team System 2005 (с установленным или без VSTO 2005 SE<sup>2</sup> )<br />— Visual Studio 2005 Professional с VSTO 2005 SE<sup>2</sup> установлено|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-разрядное только<sup>3</sup>)<br /><br /> Система Microsoft Office 2007<br /><br /> Microsoft Office 2003|Среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск|.NET Framework 2.0, .NET Framework 3.0 или .NET Framework 3.5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)][!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]приложения и включают в себя среду выполнения Visual Studio 2010 Tools for Office. Таким образом, эти приложения всегда используют среду выполнения Visual Studio 2010 Tools for Office, а не Инструменты Visual Studio для Microsoft Office системы (среда выполнения версии 3,0) в этом сценарии. Приложения в выпуске 2007 системы Microsoft Office могут использовать среду выполнения набора средств Visual Studio 2010 для Office или набор средств Visual Studio для системы Microsoft Office (версия среды выполнения: 3.0).

 2. VSTO 2005 SE — это бесплатный дополнительный компонент для Visual Studio, который предоставляет шаблоны проекта надстроек VSTO для Microsoft Office 2003 и 2007. Его можно установить вместе с Visual Studio 2005 Professional, набором средств Visual Studio 2005 для Office или выпуском в Visual Studio Team System 2005. Дополнительные сведения см. в статье [Visual Studio 2005 Tools for Office Second Edition](https://developer.microsoft.com/office/docs).

 3. Решения Office, которым требуется среда выполнения набора средств Visual Studio 2005 для Office, второй выпуск, несовместимы с 64-разрядной версией [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] и [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Для запуска этих решений в 64-разрядном выпуске [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] необходимо обновить проект до [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] или до проекта Visual Studio 2008, который ориентируется на выпуск 2007 системы Microsoft Office.

## <a name="see-also"></a>См. также раздел
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Общие сведения о Инструменты Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Инструменты Visual Studio сценариев установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Настройка компьютера для разработки решений Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
