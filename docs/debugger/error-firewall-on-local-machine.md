---
title: "Ошибка: брандмауэр на локальном компьютере | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: брандмауэр на локальном компьютере
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Брандмауэр подключения к интернету на локальном компьютере, с которого запускается Visual Studio, не настроен так, чтобы была доступна удаленная отладка.  Для удаленной отладки управляемого или машинного кода с транспортом по умолчанию, порт TCP 135 должен быть открыт для трафика DCOM.  Необходимо открыть общий доступ к файлам и принтерам, и файл devenv.exe должен быть добавлен в список исключений.  Возможно также потребуется открыть некоторые порты IPSec.  
  
 Дополнительные сведения см. в разделе [Настройка Инструментов удаленной отладки в устройстве](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).