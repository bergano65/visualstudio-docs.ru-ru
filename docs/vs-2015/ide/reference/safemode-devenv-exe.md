---
title: -SafeMode (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94e8e87f4440644f76906a70ea09a46282b109c2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670359"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Запускает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в безопасном режиме, загружая только среду и службы по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Примечания  
 Этот параметр запрещает загрузку пакетов VSPackage сторонних производителей при запуске [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], обеспечивая надежность работы.  
  
## <a name="description"></a>Описание  
 В приведенном ниже примере [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запускается в безопасном режиме.  
  
## <a name="code"></a>Код  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
