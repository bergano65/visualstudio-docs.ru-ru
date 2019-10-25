---
title: Предоставляемые службы (пакет VSPackage системы управления версиями) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13be907eeb35a2d4382fb63726c09cb2924e57e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723857"
---
# <a name="services-provided-source-control-vspackage"></a>Предоставляемые службы (пакет VSPackage системы управления версиями)
Службы — это основной механизм, с помощью которого совместно используются пакеты VSPackage и между интегрированной средой разработки (IDE) Visual Studio и установленными пакетами VSPackage. Подробное описание служб и их важность в интегрированной среде разработки Visual Studio см. в разделе[использование и предоставление служб](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Служба системы управления версиями
 Visual Studio предоставляет два уровня служб: службы на уровне IDE и службы уровня пакета. Интегрированная среда разработки Visual Studio изначально предоставляет службы уровня IDE. Пакет системы управления версиями использует некоторые из этих служб. Пакет управления версиями в качестве пакета VSPackage использует свои функции управления версиями, предоставляя собственную собственную службу управления версиями. Пакет системы управления версиями инкапсулирует набор связанных с системой управления версиями интерфейсов, реализованных в виде контракта, который может использоваться в интегрированной среде разработки Visual Studio.

## <a name="see-also"></a>См. также
- [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)