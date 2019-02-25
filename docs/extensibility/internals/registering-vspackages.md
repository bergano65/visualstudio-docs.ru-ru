---
title: Регистрация пакетов VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 426adc0cd150d5867760a8570df5777fec8260a2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601581"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] полагается на файлах pkgdef, чтобы описывать и находить VSPackage. Pkgdef-файл содержит все сведения о регистрации, в противном случае будет добавляться в системный реестр. Управляемые пакеты VSPackage регистрируются, добавление атрибутов к исходному коду и затем запустив [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) на результирующую сборку для формирования pkgdef-файл.

## <a name="in-this-section"></a>В этом разделе
- [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Описание пути загрузки для пакетов VSPackage.

- [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Объясняется, как зарегистрировать VSPackage.
