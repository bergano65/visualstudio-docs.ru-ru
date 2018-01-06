---
title: "Параметры командной строки devenv для разработки VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 18c531bb849793de184f3797067dceff4bd10199
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Параметры командной строки devenv для разработки VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]позволяет разработчикам автоматизировать задачи из командной строки при выполнении devenv.exe, файл, который запускает среду разработки Visual Studio (IDE).  
  
 Следующие задачи.  
  
-   Развертывание приложений в готовые конфигурации от вне IDE.  
  
-   Автоматически построение проектов, используя конфигурацию параметров построения или конфигурации отладки.  
  
-   Загрузка интегрированной среды разработки в определенных конфигурациях из вне IDE. Кроме того можно настроить при запуске интегрированной среды разработки.  
  
## <a name="guidelines-for-switches"></a>Рекомендации для коммутаторов  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]документация описывает командной строки devenv уровня пользователя. Дополнительные сведения см. в разделе [командной строки devenv](../ide/reference/devenv-command-line-switches.md). Devenv также поддерживает дополнительные параметры командной строки, которые могут использоваться для VSPackage разработки, развертывания и отладки.  
  
|Параметр командной строки|Описание:|  
|--------------------------|-----------------|  
|/ SafeMode|Запускает [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме, загружая только по умолчанию интегрированная среда разработки и служб. / SafeMode предотвращает всех сторонних VSPackages при загрузке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] начинается, обеспечивая стабильное выполнение.<br /><br /> У этого параметра нет аргументов.|  
|/ resetskippkgs|Очищает все пропустить параметров загрузки, добавленные пользователями, которые хотите избежать загрузки проблемный пакеты VSPackage, затем запускает [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Наличие тега SkipLoading отключает загрузку пакета VSPackage. Удаление этого тега повторно включает загрузку VSPackage.<br /><br /> У этого параметра нет аргументов.|  
|/ rootsuffix|Запускает [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с помощью альтернативное расположение. Следующая команда запускается ярлыком созданные [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] установщика:<br /><br /> devenv/rootsuffix exp<br /><br /> В этом случае exp определяет местоположение с определенным расширением, например 10.0Exp вместо версии 10.0. Экспериментальный экземпляр позволяет отлаживать VSPackage отдельно от экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] используется для написания кода.<br /><br /> Этот параметр может принимать любая строка, которая определяет местоположение, созданного с помощью VSRegEx.exe. Дополнительные сведения см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).|  
|/Splash|Показывает [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] экран-заставка обычным образом и затем отображает окно сообщения перед отображением основной интегрированной среды разработки. Окно сообщения позволяет изучить заставки для проверки продукта значком VSPackage.<br /><br /> У этого параметра нет аргументов.|  
  
## <a name="see-also"></a>См. также  
 [Добавление параметров командной строки](../extensibility/adding-command-line-switches.md)   
 [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md)