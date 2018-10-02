---
title: -ResetSkipPkgs (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e03e260662330556bff8f15a83fe747c374154b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572106"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [- ResetSkipPkgs (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetskippkgs-devenv-exe).  
  
  
Удаляет все параметры для пропуска загрузки, которые были добавлены в пакеты VSPackage пользователями, желающими исключить загрузку проблемных пакетов VSPackage, а затем запускает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Примечания  
 Наличие тега SkipLoading отключает загрузку пакета VSPackage, удаление этого тега снова включает загрузку VSPackage.  
  
## <a name="example"></a>Пример  
 Следующий пример удаляет все теги SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



