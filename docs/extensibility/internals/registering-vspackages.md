---
title: "Регистрация пакеты VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управляемых пакетов VSPackages регистрации"
  - "Регистрация управляемых пакетов VSPackages"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Регистрация пакеты VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] полагает в файлах .pkgdef для описания и найти VSPackage.  Файл .pkgdef содержит все сведения о регистрации, которые в противном случае были бы добавляются в системный реестр.  Управляемое VSPackages регистрируется путем добавления атрибутов к исходному коду, а затем выполнить [Служебная программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) в результирующей сборке, для которой создается файл .pkgdef.  
  
## В этом подразделе  
 [Указание расположения файла VSPackage к оболочке VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Описывает путь загрузки VSPackages.  
  
 [Регистрация и Отмена регистрации VSPackages.](../../extensibility/registering-and-unregistering-vspackages.md)  
 Объясняет, как зарегистрировать VSPackage.  
  
 [Использование пользовательского атрибута регистрации для регистрации расширения](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)  
 Описывает, как создать манифест регистрации, который может быть использован для развертывания управляемых VSPackage.