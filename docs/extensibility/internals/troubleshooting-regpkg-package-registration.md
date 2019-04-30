---
title: Устранение неполадок регистрации пакета RegPkg | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12beb4bda419c99c013a324b08b92bf3ff5365dd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429873"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
> [!NOTE]
> С помощью файлах pkgdef — предпочтительный способ зарегистрировать пакеты в Visual Studio. Это позволяет расширение развертывания без доступа в системный реестр. Файлов pkgdef создаются с помощью [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо использовать версию RegPkg, который подходит для вашего пакета.

## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, связанное с версиями пакета
 Существуют две версии RegPkg. Одна версия входит в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Эта версия используется для регистрации пакетов, созданных с помощью одного из следующих сборок:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Его не удалось зарегистрировать пакетов, созданных с помощью более ранних Microsoft.VisualStudio.Shell.dll сборки.

   На более раннюю версию RegPkg можно зарегистрировать пакеты, которые созданы с помощью Microsoft.VisualStudio.Shell.dll сборки. Тем не менее его не удалось зарегистрировать пакеты, созданные с помощью более поздней версии этой сборки.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)