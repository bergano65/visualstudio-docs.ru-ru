---
title: -ResetSkipPkgs (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ffc8ae23dd66cdf863b6bf193289df63b3fdb06
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Удаляет все параметры для пропуска загрузки, которые были добавлены в пакеты VSPackage пользователями, желающими исключить загрузку проблемных пакетов VSPackage, а затем запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
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