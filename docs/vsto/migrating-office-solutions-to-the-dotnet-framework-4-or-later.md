---
title: Перенос решений Office на .NET Framework 4 или более поздней версии
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 729fafd1f6dfdf889293c9686f455be8de5a81fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970381"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Перенос решений Office на .NET Framework 4 или более поздней версии
  Если требуемая версия .NET framework проекта Office изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии из более ранней версии платформы .NET Framework, некоторые дополнительные действия могут быть необходимы, чтобы продолжить выполнение решения на компьютерах разработки и конечных пользователей. Дополнительные сведения см. в разделе [необходимых изменений для выполнения проектов Office, которые переносятся на .NET Framework 4 или .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Кроме того, проект может перестать компилироваться. Некоторые функции проектов Office используют разные модели программирования для различных версий платформы .NET Framework. При изменении целевой платформы проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию необходимо внести следующие изменения в код проекта:

- [Обновление проектов Excel и Word, которые переносятся на .NET Framework 4 или .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Обновление настроек ленты в проектах Office, которые переносятся на .NET Framework 4 или .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)

- [Обновление областей формы в проектах Outlook, которые переносятся на .NET Framework 4 или .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Требуемая версия .NET Framework проекта Office изменяется при его обновлении с более ранней версии Visual Studio. Дополнительные сведения см. в разделе [обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Дополнительные сведения о том, почему некоторые компоненты проектов Office имеют другую модель программирования, при выборе [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, см. в разделе [изменения проектирования проектов Office, предназначенных для .NET Framework 4 или .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) и [средств Visual Studio для среды](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>См. также
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Практическое руководство. Определение целевой версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [Устранение ошибок в решениях Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Дополнительные сведения об ошибках в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md)
