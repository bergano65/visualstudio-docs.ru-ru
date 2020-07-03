---
title: Устранение неполадок регистрации пакета RegPkg | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65acd78ef2591a84a1f48bd6a694996f48078d68
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905126"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , необходимо использовать версию regpkg, подходящую для вашего пакета.

## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, связанные с версиями пакетов
 Существует две версии RegPkg. Одна версия включена в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Используйте эту версию для регистрации пакетов, созданных с помощью одной из следующих сборок:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Он не может зарегистрировать пакеты, созданные с помощью предыдущей Microsoft.VisualStudio.Shell.dll сборки.

   Более ранняя версия RegPkg может регистрировать пакеты, созданные с помощью сборки Microsoft.VisualStudio.Shell.dll. Однако он не может зарегистрировать пакеты, созданные с помощью более поздних версий этой сборки.

## <a name="see-also"></a>Дополнительно
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)
