---
title: Регистрация пакетов VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c826b61e4f6d2255be7b7fdad967bab0d8dea74
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561426"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [регистрации пакетов VSPackage](https://docs.microsoft.com/visualstudio/extensibility/internals/registering-vspackages).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] полагается на файлах pkgdef, чтобы описывать и находить VSPackage. Pkgdef-файл содержит все сведения о регистрации, в противном случае будет добавляться в системный реестр. Управляемые пакеты VSPackage регистрируются, добавление атрибутов к исходному коду и затем запустив [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) на результирующую сборку для формирования pkgdef-файл.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Описание пути загрузки для пакетов VSPackage.  
  
 [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Объясняется, как зарегистрировать VSPackage.  
  
 [Использование пользовательского атрибута регистрации для регистрации расширения](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Описывает способ создания манифеста регистрации, который может использоваться для развертывания управляемого пакета VSPackage.

