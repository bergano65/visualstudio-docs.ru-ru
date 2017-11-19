---
title: "Регистрация пакетов VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d580d3d74d8648b7181ac1ca384d3232fa8225b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]использует файлы .pkgdef для описания и найдите пакет VSPackage. Pkgdef-файл содержит все сведения о регистрации, в противном случае следует добавить в системный реестр. Добавление атрибутов в исходный код, а затем выполнив зарегистрированные управляемые пакеты VSPackage [CreatePkgDef программы](../../extensibility/internals/createpkgdef-utility.md) в результирующей сборке, для создания pkgdef-файл.  
  
## <a name="in-this-section"></a>Содержание  
 [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Описание пути загрузки для пакетов VSPackage.  
  
 [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Объясняет, как зарегистрировать VSPackage.  
