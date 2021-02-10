---
title: Перенос решений Office на платформа .NET Framework 4 или более поздней версии
description: Узнайте, как можно перенести решения Office на платформа .NET Framework 4 или более поздней версии, чтобы проект продолжал работать.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8c11b2f107414ac5ffb048d7c5e49609ba0b17b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946141"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Перенос решений Office на платформа .NET Framework 4 или более поздней версии
  Если целевая платформа проекта Office изменена на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя из более ранней версии платформа .NET Framework, может потребоваться выполнить некоторые дополнительные действия, чтобы продолжить выполнение решения на компьютерах разработки и конечных пользователей. Дополнительные сведения см. в разделе [необходимые изменения для запуска проектов Office, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Кроме того, проект может перестать компилироваться. Некоторые функции проектов Office используют разные модели программирования для различных версий платформы .NET Framework. При изменении целевой платформы проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию необходимо внести следующие изменения в код проекта:

- [Обновление проектов Excel и Word, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Обновление настроек ленты в проектах Office, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Обновление областей формы в проектах Outlook, переносимых на платформа .NET Framework 4 или платформа .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Требуемая версия .NET Framework проекта Office изменяется при его обновлении с более ранней версии Visual Studio. Дополнительные сведения см. в статье [обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Дополнительные сведения о том, почему некоторые функции в проектах Office имеют другую модель программирования при использовании [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, см. в разделе [изменения в проектировании проектов Office, предназначенных для платформа .NET Framework 4, а также в](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) статье [Общие сведения о среде выполнения Office для](../vsto/visual-studio-tools-for-office-runtime-overview.md)платформа .NET Framework 4,5 и инструменты Visual Studio.

## <a name="see-also"></a>См. также раздел
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Практическое руководство. Определение целевой версии .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Устранение ошибок в решениях Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Дополнительная поддержка ошибок в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md)
