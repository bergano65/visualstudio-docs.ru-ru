---
title: Устранение неполадок регистрации пакета RegPkg | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722277"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо использовать версию RegPkg, подходящую для вашего пакета.

## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, связанные с версиями пакетов
 Существует две версии RegPkg. Одна из версий включена в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Используйте эту версию для регистрации пакетов, созданных с помощью одной из следующих сборок:

1. Microsoft. Висуалстудиошелл. 9.0. dll

2. Microsoft. Висуалстудиошелл. 10.0. dll

3. Microsoft. Висуалстудиошелл. 11.0. dll

   Он не может зарегистрировать пакеты, созданные с помощью предыдущей сборки Microsoft. VisualStudio. Shell. dll.

   Более ранняя версия RegPkg может регистрировать пакеты, созданные с помощью сборки Microsoft. VisualStudio. Shell. dll. Однако он не может зарегистрировать пакеты, созданные с помощью более поздних версий этой сборки.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)