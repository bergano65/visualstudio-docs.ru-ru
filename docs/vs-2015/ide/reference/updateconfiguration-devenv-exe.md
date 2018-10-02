---
title: -Updateconfiguration (devenv.exe) | Документы Майкрософт
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
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31fd7f52ad2be89a3e6a40a76948aea0d8cc8bfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561694"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [- Updateconfiguration (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/updateconfiguration-devenv-exe).  
  
  
Предписывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в системе и проверить наличие изменений в кэше MEF.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполняет эту команду автоматически при установке пакета VSIX. После исправления файлов следует выполнить команду `devenv.exe /updateconfiguration`, чтобы среда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] обновила кэш MEF. Это позволит оценить достаточность исправления.  
  
## <a name="example"></a>Пример  
 Приведенная ниже команда предписывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в системе и проверить наличие изменений в кэше MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



