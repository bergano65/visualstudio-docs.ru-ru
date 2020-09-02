---
title: Регистрация пакетов VSPackage | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705747"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует файлы pkgdef для описания и размещения VSPackage. Файл pkgdef содержит все сведения о регистрации, которые в противном случае были бы добавлены в системный реестр. Управляемые пакеты VSPackage регистрируются путем добавления атрибутов в исходный код, а затем запуска [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) в результирующей сборке для создания файла pkgdef.

## <a name="in-this-section"></a>в этом разделе
- [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Описывает путь загрузки пакетов VSPackage.

- [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Описание процесса регистрации VSPackage.
