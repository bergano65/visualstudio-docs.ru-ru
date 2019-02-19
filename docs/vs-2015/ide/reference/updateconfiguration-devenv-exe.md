---
title: -Updateconfiguration (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9e058d18c0a7c6d1d3b26a5b379c308d26f790ca
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783165"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>См. также раздел  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
