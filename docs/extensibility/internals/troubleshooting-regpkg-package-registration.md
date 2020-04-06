---
title: Неполадки RegPkg Регистрация пакета (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704332"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
> [!NOTE]
> Предпочтительным способом регистрации пакетов в Visual Studio является использование файлов .pkgdef. Это позволяет развертывать расширение без доступа к реестру системы. Файлы Pkgdef создаются с помощью [Утилиты CreatePkgDef.](../../extensibility/internals/createpkgdef-utility.md)

 Чтобы зарегистрировать пакет с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]RegPkg в, вы должны использовать версию RegPkg, которая подходит для вашего пакета.

## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg Версии, связанные с пакетными версиями
 Есть две версии RegPkg. Одна из версий включена в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Используйте эту версию для регистрации пакетов, которые были построены с помощью одной из следующих сборок:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Он не может зарегистрировать пакеты, которые были построены с помощью предыдущей сборки Microsoft.VisualStudio.Shell.dll.

   Более ранняя версия RegPkg может зарегистрировать пакеты, которые были построены с помощью сборки Microsoft.VisualStudio.Shell.dll. Однако он не может регистрировать пакеты, построенные с помощью более поздних версий этой сборки.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)
