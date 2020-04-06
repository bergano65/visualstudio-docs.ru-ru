---
title: Регистрация VSPackages Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705747"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]опирается на файлы .pkgdef для описания и поиска VSPackage. Файл .pkgdef содержит всю регистрационную информацию, которая в противном случае была бы добавлена в системный реестр. Управляемые VSPackages регистрируются путем добавления атрибутов к исходному коду, а затем запуска [утилиты CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) на результирующей сборке для создания файла .pkgdef.

## <a name="in-this-section"></a>В этом разделе
- [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Описывает траекторию погрузки для VSPackages.

- [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Объясняет, как зарегистрировать VSPackage.
