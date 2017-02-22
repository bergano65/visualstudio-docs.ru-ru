---
title: "/Edit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Edit - параметр Devenv"
  - "Devenv, /edit - параметр"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открытие заданного файла в существующем экземпляре приложения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Синтаксис  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## Аргументы  
 `file1`  
 Необязательный.  Файл, который необходимо открыть в существующем экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Если экземпляр приложения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отсутствует, то создается новый экземпляр с упрощенной структурой окна, и файл `file1` открывается в новом экземпляре.  
  
 `file2`  
 Необязательный.  Один или несколько дополнительных файлов, которые необходимо открыть в существующем экземпляре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Заметки  
 Если файл не указан, а экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] существует, фокус передается существующему экземпляру [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Если файл не указан, а экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отсутствует, создается новый экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с упрощенной структурой окна.  
  
 Если существующий экземпляр приложения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находится в модальном состоянии, например в случае открытия [диалогового окна параметров](../../ide/reference/options-dialog-box-visual-studio.md), файл будет открыт в существующем экземпляре после того, как приложение [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выйдет из модального состояния.  
  
## Пример  
 В приведенном ниже примере файл `MyFile.cs` открывается в существующем экземпляре приложения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], или, в случае отсутствия этого экземпляра, создается новый экземпляр [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv /edit MyFile.cs  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)