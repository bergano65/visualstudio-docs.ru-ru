---
title: -SafeMode (devenv.exe) | Документы Майкрософт
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b785a3e43726522f6e6cc6ce99dec4bf3815c81d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230084"
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
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



