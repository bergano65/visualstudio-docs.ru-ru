---
title: "-Updateconfiguration (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93efd5d0e0eb391a164f4997b7ddeedab09b4201
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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