---
title: Предоставляемые услуги (Источник управления VSPackage) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705411"
---
# <a name="services-provided-source-control-vspackage"></a>Предоставляемые службы (пакет VSPackage системы управления версиями)
Услуги являются основным механизмом, с помощью которого функциональность распределяется между VSPackages и между визуальной студии интегрированной среды разработки (IDE) и установленных VSPackages. Подробное описание услуг и их важности в Visual Studio IDE смотрите[Использование и предоставление услуг.](../../extensibility/using-and-providing-services.md)

## <a name="the-source-control-service"></a>Служба управления источниками
 Visual Studio предоставляет два уровня услуг, услуги уровня IDE и услуги уровня пакетов. Visual Studio IDE на родине предоставляет услуги уровня IDE. Пакет управления исходом потребляет некоторые из этих услуг. Пакет управления исходным источником в виде VSPackage делится функциональностью управления исходным сообщением, предоставляя собственную службу управления частными источниками. Пакет управления исходным элементом инкапсулирует набор интерфейсов, связанных с исходным управлением, реализованных им в виде контракта, который может быть использован Visual Studio IDE.

## <a name="see-also"></a>См. также
- [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)
