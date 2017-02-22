---
title: "Регистрация расширений платформы .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "диалоговое окно «Добавление ссылок», регистрация расширений платформы .NET Framework"
  - "MSBuild, регистрация расширений платформы .NET Framework"
  - "расширения .NET Framework, регистрация"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Регистрация расширений платформы .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Разработчик может создать сборку, расширяющую определенную версию платформы .NET Framework.  Чтобы отобразить сборку в диалоговом окне Visual Studio **Добавление ссылок**, необходимо добавить ее родительскую папку в системный реестр.  
  
 Например, предположим, что компания Trey Research разработала библиотеку, которая расширяет платформу .NET Framework 4. При этом сборки библиотеки должны отображаться в диалоговом окне **Добавление ссылок** при разработке проекта для платформы .NET Framework 4.  Также предположим, что сборки установлены в папке C:\\TreyResearch\\Extensions4\\, являются 64\-разрядными и выполняются на 64\-разрядном компьютере или являются 32\-разрядными и выполняются на 32\-разрядном компьютере.  
  
 Зарегистрируйте эту папку с помощью следующего раздела: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  Присвойте этому разделу значение по умолчанию C:\\TreyResearch\\Extensions4.  
  
> [!NOTE]
>  Номер построения версии .NET Framework может быть другим.  
  
 Чтобы зарегистрировать 32\-разрядную сборку на 64\-разрядном компьютере, используйте узел Wow6432, например: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  
  
## См. также  
 [Интеграция Visual Studio](../msbuild/visual-studio-integration-msbuild.md)