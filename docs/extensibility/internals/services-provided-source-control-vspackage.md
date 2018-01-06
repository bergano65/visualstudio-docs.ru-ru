---
title: "Службы, предоставляемые (VSPackage управления источника) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6951881e915b44c0cb0c85685280f2b770647f3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="services-provided-source-control-vspackage"></a>Службы, предоставляемые (VSPackage управления источника)
Службы являются основным механизмом, через который общие функциональные возможности среди пакетов VSPackage, а также между Visual Studio интегрированной среды разработки (IDE) и его установленных пакетов VSPackage. Подробное описание службы и их важности в Интегрированной среде разработки Visual Studio см. в разделе[использование и предоставление службы](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Систему управления версиями  
 Visual Studio предоставляет два уровня службы, службы интегрированной среды разработки уровня и уровня пакета. По умолчанию, в Интегрированной среде разработки Visual Studio предоставляют интегрированной среды разработки уровня служб. Пакет системы управления версиями использует некоторые из этих служб. Пакет системы управления версиями, как VSPackage использует его функций системы управления версиями, предоставляя свои собственные службы управления частного источника. Пакет системы управления версиями инкапсулирует набор источника связанные с управлением интерфейсов, реализованных в виде контракта, который можно использовать в интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)