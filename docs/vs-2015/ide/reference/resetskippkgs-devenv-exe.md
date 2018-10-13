---
title: -ResetSkipPkgs (devenv.exe) | Документы Майкрософт
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
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2345c675f55be5c01ea65f5266d4b73bff30feed
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190376"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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



