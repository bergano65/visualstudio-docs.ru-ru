---
title: "-Updateconfiguration (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 741deb2d7ddb86e0a0dc0246b1c53f497d0ab5f8
ms.lasthandoff: 02/22/2017

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
Предписывает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в системе и проверить наличие изменений в кэше MEF.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выполняет эту команду автоматически при установке пакета VSIX. После исправления файлов следует выполнить команду `devenv.exe /updateconfiguration`, чтобы среда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обновила кэш MEF. Это позволит оценить достаточность исправления.  
  
## <a name="example"></a>Пример  
 Приведенная ниже команда предписывает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выполнить слияние пакетов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в системе и проверить наличие изменений в кэше MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
