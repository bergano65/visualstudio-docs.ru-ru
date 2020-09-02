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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157390"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] использует файлы pkgdef для описания и размещения VSPackage. Файл pkgdef содержит все сведения о регистрации, которые в противном случае были бы добавлены в системный реестр. Управляемые пакеты VSPackage регистрируются путем добавления атрибутов в исходный код, а затем запуска [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) в результирующей сборке для создания файла pkgdef.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Описывает путь загрузки пакетов VSPackage.  
  
 [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Описание процесса регистрации VSPackage.  
  
 [Использование пользовательского атрибута регистрации для регистрации расширения](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Описывает создание манифеста регистрации, который можно использовать для развертывания управляемого пакета VSPackage.
