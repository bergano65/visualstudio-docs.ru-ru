---
title: Службы, предоставляемые (пакет VSPackage управления версиями) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee980b74415d906a5c48cfd5ad1e20e7b5544320
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273381"
---
# <a name="services-provided-source-control-vspackage"></a>Предоставляемые службы (пакет VSPackage системы управления версиями)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Службы являются основным механизмом, через который функциональность становится общей среди пакетов VSPackage, а также между Интегрированной среды разработки Visual Studio и его установленных пакетов VSPackage. Подробное описание служб и их важности в Интегрированной среде разработки Visual Studio, см. в разделе[использование и предоставление службы](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Службы управления версиями  
 Visual Studio предоставляет два уровня службы, службы уровня интегрированной среды разработки и уровня пакета. В собственном коде, в интегрированной среде разработки Visual Studio обеспечивает службы уровня интегрированной среды разработки. Пакет системы управления версиями использует некоторые из этих служб. Пакет системы управления версиями, как VSPackage общих папок его функции системы управления версиями, предоставляя в закрытый систему управления версиями, свои собственные. Пакет системы управления версиями инкапсулирует набор источника связанные с управлением версиями интерфейсов, реализованных в виде контракт, который может использоваться в интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)

