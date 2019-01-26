---
title: Службы, предоставляемые (пакет VSPackage управления версиями) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f94efff27ea45dc070e34f26d85be4bd7ff5b50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936909"
---
# <a name="services-provided-source-control-vspackage"></a>Предоставляемые службы (пакет VSPackage системы управления версиями)
Службы являются основным механизмом, через который функциональность становится общей среди пакетов VSPackage, а также между Интегрированной среды разработки Visual Studio и его установленных пакетов VSPackage. Подробное описание служб и их важности в Интегрированной среде разработки Visual Studio, см. в разделе[использование и предоставление службы](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Службы управления версиями  
 Visual Studio предоставляет два уровня службы, службы уровня интегрированной среды разработки и уровня пакета. В собственном коде, в интегрированной среде разработки Visual Studio обеспечивает службы уровня интегрированной среды разработки. Пакет системы управления версиями использует некоторые из этих служб. Пакет системы управления версиями, как VSPackage общих папок его функции системы управления версиями, предоставляя в закрытый систему управления версиями, свои собственные. Пакет системы управления версиями инкапсулирует набор источника связанные с управлением версиями интерфейсов, реализованных в виде контракт, который может использоваться в интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)