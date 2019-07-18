---
title: Регистрация пакетов VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ac51f23132d855c3da921cc2743c3064a353524
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331320"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] полагается на файлах pkgdef, чтобы описывать и находить VSPackage. Pkgdef-файл содержит все сведения о регистрации, в противном случае будет добавляться в системный реестр. Управляемые пакеты VSPackage регистрируются, добавление атрибутов к исходному коду и затем запустив [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) на результирующую сборку для формирования pkgdef-файл.

## <a name="in-this-section"></a>В этом разделе
- [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Описание пути загрузки для пакетов VSPackage.

- [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Объясняется, как зарегистрировать VSPackage.
