---
title: Службы, предоставляемые (VSPackage управления источника) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a52ffa7067a91582d8bfe31e09d6b03be54c4ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129606"
---
# <a name="services-provided-source-control-vspackage"></a>Службы, предоставляемые (VSPackage управления источника)
Службы являются основным механизмом, через который общие функциональные возможности среди пакетов VSPackage, а также между Visual Studio интегрированной среды разработки (IDE) и его установленных пакетов VSPackage. Подробное описание службы и их важности в Интегрированной среде разработки Visual Studio см. в разделе[использование и предоставление службы](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Систему управления версиями  
 Visual Studio предоставляет два уровня службы, службы интегрированной среды разработки уровня и уровня пакета. По умолчанию, в Интегрированной среде разработки Visual Studio предоставляют интегрированной среды разработки уровня служб. Пакет системы управления версиями использует некоторые из этих служб. Пакет системы управления версиями, как VSPackage использует его функций системы управления версиями, предоставляя свои собственные службы управления частного источника. Пакет системы управления версиями инкапсулирует набор источника связанные с управлением интерфейсов, реализованных в виде контракта, который можно использовать в интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)