---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
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
  - "/ResetSettings - параметр Devenv"
  - "Devenv, /ResetSettings - параметр"
  - "ResetSettings - параметр"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Восстанавливает параметры [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] по умолчанию и автоматически запускает IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  При необходимости выполняется сброс параметров в соответствии с указанным файлом .vssettings.  
  
 Параметры по умолчанию определяются профилем, выбранным при первом запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Синтаксис  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## Аргументы  
 `SettingsFile`  
 Полный путь и имя файла .vssettings с параметрами для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Для восстановления профиля обычных параметров среды разработки используйте `General`.  
  
## Заметки  
 Если параметр `SettingsFile` не указан, при следующем запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] будет предложено выбрать коллекцию параметров по умолчанию.  
  
## Пример  
 В приведенной командной строке показано применение параметров, сохраненных в файле `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## См. также  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)