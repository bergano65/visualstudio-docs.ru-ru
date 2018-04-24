---
title: -SafeMode (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c8748a6dadaee41a5e615742715a92240b74ab8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Запускает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в безопасном режиме, загружая только среду и службы по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Примечания  
 Этот параметр запрещает загрузку пакетов VSPackage сторонних производителей при запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], обеспечивая надежность работы.  
  
## <a name="description"></a>Описание:  
 В приведенном ниже примере [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается в безопасном режиме.  
  
## <a name="code"></a>Код  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)