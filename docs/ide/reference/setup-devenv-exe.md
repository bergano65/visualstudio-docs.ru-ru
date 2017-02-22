---
title: "-Setup (devenv.exe) | Microsoft Docs"
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
  - "setup Devenv - коммутатор"
  - "/setup Devenv - коммутатор"
  - "Devenv, параметр /setup"
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Заставляет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выполнить слияние метаданных ресурсов, описывающих меню, панели инструментов и группы команд, из всех доступных пакетов VSPackage.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Примечания  
 У этого параметра нет аргументов. Команда `devenv /setup` обычно выдается в качестве последнего этапа процесса установки. Использование параметра `/setup` не приводит к запуску [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Для использования параметров `devenv` и [devenv](../../ide/reference/setup-devenv-exe.md) нужно запустить [devenv](../../ide/reference/installvstemplates-devenv-exe.md) от имени администратора.  
  
## <a name="example"></a>Пример  
 В этом примере показан последний этап установки версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], включающей пакеты VSPackage.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)