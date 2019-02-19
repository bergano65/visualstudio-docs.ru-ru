---
title: -Setup (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0df3b74b6c5acc4b8630dcf5759dd3fd6e7a1afe
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54805369"
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
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
