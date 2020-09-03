---
title: Управляемый справочник (разработка решений Office в Visual Studio)
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29e8a2206432555e58b47691233bd46c49791046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519864"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Управляемый справочник (разработка решений Office в Visual Studio)
  В этом разделе содержится справочная документация по API для пространств имен и типов, используемых в проектах Office, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](includes/net-v45-md.md)]. Справочную документацию по API о пространствах имен и типах, используемых в проектах Office, предназначенных для .NET Framework 3,5, см. в следующем справочном разделе документации по Visual Studio: [управляемый справочник (разработка решений Office в Visual Studio)](managed-reference-office-development-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>В этом разделе
 <xref:Microsoft.Office.Tools>

 Содержит классы, общие для программирования решений Office. К ним относятся базовый класс для надстроек VSTO, классы для создания настраиваемых областей задач в настройках VSTO, классы для создания смарт-тегов в решениях Word и Excel и классы для создания панелей действий в настройках уровня документа.

 <xref:Microsoft.Office.Tools.Excel>

 Содержит элементы управления ведущего приложения и ведущие элементы, которые могут использоваться в решениях для Excel.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Содержит элементы управления Excel и элементы управления Windows Forms, которые могут использоваться в решениях для Excel.

 <xref:Microsoft.Office.Tools.Outlook>

 Содержит классы, используемые надстройками VSTO для Outlook, включая классы, используемые для создания настраиваемых областей формы.

 <xref:Microsoft.Office.Tools.Ribbon>

 Содержит классы, используемые для программного изменения настроек ленты, созданных с помощью конструктора лент.

 <xref:Microsoft.Office.Tools.Word>

 Содержит элементы управления ведущего приложения и ведущие элементы, которые могут использоваться в решениях для Word.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Содержит элементы управления Word и элементы управления Windows Forms, которые могут использоваться в решениях для Word.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Содержит класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> и набор связанных классов кэшированных данных. Эти классы могут использоваться для изменения некоторых аспектов настроек уровня документа на компьютерах, на которых не установлен Microsoft Office.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Содержит интерфейс <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> (который можно реализовать для создания *действий, выполняемых после развертывания* , для решения Office), исключения, которые могут возникать при установке решения Office, и другие API, которые являются частью инфраструктуры Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Содержит основные исключения, которые могут создаваться [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)], несколько классов, которые могут использоваться для кэширования данных в настройках уровня документа, и другие API, являющиеся частью инфраструктуры Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Содержит классы задач MSBuild, которые используются для сборки проектов Office.

## <a name="see-also"></a>См. также раздел
- [Обзор средств Visual Studio для среды выполнения Office](visual-studio-tools-for-office-runtime-overview.md)
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)
- [Примеры и пошаговые руководства по разработке решений Office](office-development-samples-and-walkthroughs.md)
- [Разработка и создание решений Office](designing-and-creating-office-solutions.md)
