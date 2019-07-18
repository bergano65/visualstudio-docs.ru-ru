---
title: Регистрация пакетов VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157390"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] полагается на файлах pkgdef, чтобы описывать и находить VSPackage. Pkgdef-файл содержит все сведения о регистрации, в противном случае будет добавляться в системный реестр. Управляемые пакеты VSPackage регистрируются, добавление атрибутов к исходному коду и затем запустив [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) на результирующую сборку для формирования pkgdef-файл.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Описание пути загрузки для пакетов VSPackage.  
  
 [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Объясняется, как зарегистрировать VSPackage.  
  
 [Использование пользовательского атрибута регистрации для регистрации расширения](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Описывает способ создания манифеста регистрации, который может использоваться для развертывания управляемого пакета VSPackage.
