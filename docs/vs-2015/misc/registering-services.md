---
title: Регистрация служб | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564270"
---
# <a name="registering-services"></a>Регистрация служб
Для поддержки загрузки по требованию, поставщик услуг должен зарегистрировать глобальные службы с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Во время разработки поставщики управляемых служб регистрируют службы и переопределения служб путем добавления атрибутов к исходному коду для пакетов и затем выполняют сборку пакетов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среды разработки. Это запускает служебную программу RegPkg.exe в результирующей сборке, регистрируя пакет и подготавливая его к развертыванию. Дополнительные сведения см. в разделе [как: зарегистрировать службу](../misc/how-to-register-a-service.md).  
  
 Поставщики неуправляемых служб необходимо зарегистрировать службы, они предоставляют [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в службах раздел "или" переопределения раздел системного реестра. В следующем фрагменте REG-файла показано, как служба SVsTextManager может быть зарегистрирована:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 В приведенном выше примере номер версии — версия [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], такие как 7.1 или 8.0, ключ {F5E7E71D-1401-11d1-883B-0000F87579D2} является идентификатором службы (SID) службы, SVsTextManager и {значение по умолчанию F5E7E720-1401-11D1-883B-0000F87579D2} является GUID диспетчера текстов VSPackage, который предоставляет службу пакета.  
  
## <a name="remote-services-and-background-threads"></a>Удаленные службы и фоновые потоки  
 Службы, которые вы предоставляете, не предоставляются автоматически удаленно или в фоновые потоки. Чтобы сделать их доступными, вам нужно выполнить сборку и зарегистрировать библиотеку типов.  
  
 Из неуправляемого кода, который использует библиотеку Visual Studio (VSL), вы можете зарегистрировать свою библиотеку типов следующим образом:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Из управляемого кода вы можете добавить действие после сборки следующим образом:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>См. также  
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)