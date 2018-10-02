---
title: -SafeMode (devenv.exe) | Документы Майкрософт
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 308dd7e81a35604bcd0f6f5eba517b850ace17ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564177"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [- SafeMode (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/safemode-devenv-exe).  
  
  
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
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



