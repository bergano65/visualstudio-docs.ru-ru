---
title: "Не удается восстановить связи файлов по умолчанию. Примечание. Чтобы изменить связи файлов, необходимо обладать правами администратора или опытного пользователя на этом компьютере. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Не удается восстановить связи файлов по умолчанию. Примечание. Чтобы изменить связи файлов, необходимо обладать правами администратора или опытного пользователя на этом компьютере.
Эта ошибка возникает при использовании параметра командной строки devenv \/AssociateFiles, однако с текущими правами пользователя нельзя получить доступ к разделу HKEY\_CLASSES\_ROOT реестра. При запуске [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] необходимо выполнить команду devenv с правами администратора, чтобы воспользоваться параметром \/AssociateFiles \(devenv.exe\).  
  
### Исправление ошибки  
  
-   Воспользуйтесь учетными данными администратора и повторите попытку.  
  
## См. также  
 [User Rights and Visual Studio](http://msdn.microsoft.com/ru-ru/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md)