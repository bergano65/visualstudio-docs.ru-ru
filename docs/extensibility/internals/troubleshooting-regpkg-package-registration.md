---
title: Устранение неполадок регистрации пакета RegPkg | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137122"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок RegPkg пакета регистрации
> [!NOTE]
>  С помощью файлов .pkgdef — предпочтительный способ регистрации пакетов в Visual Studio. Это обеспечивает расширение развертывания без необходимости доступа к реестру системы. Pkgdef файлы создаются с помощью [CreatePkgDef программы](../../extensibility/internals/createpkgdef-utility.md).  
  
 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо использовать версию RegPkg, которая подходит для вашего пакета.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, относящиеся к версии пакета  
 Существуют две версии RegPkg. Одна версия включается в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Данную версию можно используйте для регистрации пакетов, созданных с помощью одного из следующих сборок:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Его не удалось зарегистрировать пакеты, построенных с помощью более ранних Microsoft.VisualStudio.Shell.dll сборки.  
  
 Более раннюю версию RegPkg можно зарегистрировать пакеты, построенных с помощью Microsoft.VisualStudio.Shell.dll сборки. Однако его не удалось зарегистрировать пакетов, созданных с помощью более поздней версии этой сборки.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)