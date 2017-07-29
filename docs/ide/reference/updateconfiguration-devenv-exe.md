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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 6e74ef38969cb62790629b34041ceef535ff6f9e
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

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
 [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
