---
title: Предоставляемые службы (пакет VSPackage системы управления версиями) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 750710cdc381573f8aa6fd064e1fc980030cf359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202705"
---
# <a name="services-provided-source-control-vspackage"></a>Предоставляемые службы (пакет VSPackage системы управления версиями)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Службы — это основной механизм, с помощью которого совместно используются пакеты VSPackage и между интегрированной средой разработки (IDE) Visual Studio и установленными пакетами VSPackage. Подробное описание служб и их важность в интегрированной среде разработки Visual Studio см. в разделе[использование и предоставление служб](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Служба системы управления версиями  
 Visual Studio предоставляет два уровня служб: службы на уровне IDE и службы уровня пакета. Интегрированная среда разработки Visual Studio изначально предоставляет службы уровня IDE. Пакет системы управления версиями использует некоторые из этих служб. Пакет управления версиями в качестве пакета VSPackage использует свои функции управления версиями, предоставляя собственную собственную службу управления версиями. Пакет системы управления версиями инкапсулирует набор связанных с системой управления версиями интерфейсов, реализованных в виде контракта, который может использоваться в интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также:  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)
