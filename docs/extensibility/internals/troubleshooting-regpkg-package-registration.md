---
title: "Устранение неполадок регистрация пакета RegPkg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Устранение неполадок регистрация пакета RegPkg
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  С помощью файлов .pkgdef — предпочтительный способ регистрации пакетов в Visual Studio. Это обеспечивает развертывание расширения без необходимости доступа к реестру системы. Pkgdef файлы создаются с помощью [Служебная программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо использовать версию RegPkg, который подходит для вашего пакета.  
  
## Версии RegPkg, относящиеся к версии пакета  
 Существует две версии RegPkg. Одна версия включена в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Эту версию можно используйте для регистрации пакетов, созданных с помощью одного из следующих сборок:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Он не может зарегистрировать пакетов, созданных с помощью более ранних Microsoft.VisualStudio.Shell.dll сборки.  
  
 Более ранние версии RegPkg можно зарегистрировать пакетов, созданных с помощью Microsoft.VisualStudio.Shell.dll сборки. Однако он не может зарегистрировать пакетов, созданных с помощью более поздней версии этой сборки.  
  
## См. также  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)