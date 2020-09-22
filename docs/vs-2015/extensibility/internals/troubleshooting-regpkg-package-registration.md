---
title: Устранение неполадок регистрации пакета RegPkg | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842816"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , необходимо использовать версию regpkg, подходящую для вашего пакета.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, связанные с версиями пакетов  
 Существует две версии RegPkg. Одна версия включена в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Используйте эту версию для регистрации пакетов, созданных с помощью одной из следующих сборок:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Он не может зарегистрировать пакеты, созданные с помощью предыдущей Microsoft.VisualStudio.Shell.dll сборки.  
  
   Более ранняя версия RegPkg может регистрировать пакеты, созданные с помощью сборки Microsoft.VisualStudio.Shell.dll. Однако он не может зарегистрировать пакеты, созданные с помощью более поздних версий этой сборки.  
  
## <a name="see-also"></a>См. также:  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)
