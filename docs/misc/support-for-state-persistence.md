---
title: "Поддержка сохранения состояния | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сохранение состояния, поддержка managed package framework"
  - "managed package framework, поддержка сохранения состояния"
  - "состояние, сохранение"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Поддержка сохранения состояния
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] может поддерживать состояние общих объектов.  Например, решение и свойства проекта сохраняются и получаются из решений и файлов проекта.  Параметры пользователей можно экспортировать и импортировать из файлов параметров.  
  
 VSPackages обычно основана на локальном жестком диске или в системном реестре или в папке данных приложения для текущего пользователя или компьютере.  Значения, которые требует небольшого объема пространства для хранения, такие как целые числа и строки, обычно хранятся в реестре системы.  Значения, которые требуют лотов места для хранения, как растровые изображения, сохраняются в файле.  Сам путь файла могут быть сохранены в реестре системы.  Механизм сохраняемости должен иметь разрешение на доступ к локальное хранилище.  
  
## Поддержка найти локальное хранилище  
 <xref:Microsoft.VisualStudio.Shell.Package> класс обеспечивает поддержку поиска сведений о состоянии в папке реестра для данных приложения или системы для текущего пользователя или компьютера.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Возвращает корневой путь реестра локального компьютера [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например HKEY\_LOCAL\_MACHINE \\ software \\ microsoft \\ VisualStudio \\ 8.0Exp.  
  
 Корневой элемент реестра получен из локального <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> служба.  Если это недоступен, то оно получено из <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> атрибут VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Возвращает корневой путь реестра текущего пользователя \(компьютер\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например HKEY\_CURRENT\_USER \\ software \\ microsoft \\ VisualStudio \\ 8.0Exp.  
  
 Корневой элемент реестра получен из локального <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> служба.  Если это недоступен, то оно получено из атрибута DefaultLocalRegistryRoot VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Возвращает путь к каталогу, служащий общим хранилищем [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] данные для текущего перемещающегося пользователя, например C:\\Documents and Settings\\*YourAccountName*Application \\ data \\ microsoft \\ VisualStudio \\ 8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Возвращает путь к каталогу, служащий общим хранилищем [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] данные текущего пользователя non\-роуминга, например C:\\Documents and Settings\\*YourAccountName*Локальные параметры \\ data \\ application \\ microsoft \\ VisualStudio \\ 8.0Exp.  
  
## См. также  
 [Состояние VSPackage](/visual-cpp/misc/vspackage-state)