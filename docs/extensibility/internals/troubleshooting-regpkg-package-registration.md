---
title: "Устранение неполадок регистрации пакета RegPkg | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5651e7c00abe91ec8e4cae7b720b6534318051f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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