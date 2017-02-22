---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
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
  - "/upgrade - параметр Devenv"
  - "Devenv, /upgrade - параметр"
  - "upgrade - параметр Devenv"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Обновление файла решения и всех его файлов проекта или указанного файла проекта до текущих форматов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для этих файлов.  
  
## Синтаксис  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## Аргументы  
 `SolutionFile`  
 Требуется при обновлении всего решения и его проектов.  Путь и имя файла решения.  Пользователь может ввести только имя файла решения или полный путь и имя файла решения.  Если указанные папка или файл не существуют, они будут созданы.  
  
 `ProjectFile`  
 Требуется при обновлении одного проекта.  Полный путь и имя файла проекта в решении.  Пользователь может ввести только имя файла проекта или полный путь и имя файла проекта.  Если указанные папка или файл не существуют, они будут созданы.  
  
## Заметки  
 Резервные копии автоматически создаются и копируются в каталог резервных копий \(Backup\), который создается в текущем каталоге.  
  
 Решения или проекты, для которых используется система управления версиями, должны быть извлечены, прежде чем их можно будет обновлять.  
  
 Использование переключателя `/upgrade` не запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Результаты обновления можно просмотреть в разделе "Отчет об обновлении" для языка программирования решения или проекта.  Сообщения об ошибках или сведения об использовании не возвращаются.  Дополнительные сведения относительно обновления проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] см. в разделе [Практическое руководство. Устранение неполадок, связанных с неудачными обновлениями проектов Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## Пример  
 В приведенном примере выполняется обновление файла решения с именем "MyProject.sln" в папке по умолчанию для решений [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## См. также  
 [Практическое руководство. Устранение неполадок, связанных с неудачными обновлениями проектов Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)