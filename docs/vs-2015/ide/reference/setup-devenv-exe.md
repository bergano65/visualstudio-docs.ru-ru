---
title: -Setup (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f57de02f0d46a14574ef3f34d47f2f5e4018096b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230626"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Заставляет [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние метаданных ресурсов, описывающих меню, панели инструментов и группы команд, из всех доступных пакетов VSPackage.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Примечания  
 У этого параметра нет аргументов. Команда `devenv /setup` обычно выдается в качестве последнего этапа процесса установки. Использование параметра `/setup` не приводит к запуску [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Для использования параметров `devenv` и [devenv](../../ide/reference/setup-devenv-exe.md) нужно запустить [devenv](../../ide/reference/installvstemplates-devenv-exe.md) от имени администратора.  
  
## <a name="example"></a>Пример  
 В этом примере показан последний этап установки версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], включающей пакеты VSPackage.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



