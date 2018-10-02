---
title: Параметры командной строки devenv для разработки VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb10653a784b6d481717965e68b445c24b3f3db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564024"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Параметры командной строки для команды devenv для разработки VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [переключателей командной строки Devenv для разработки VSPackage](https://docs.microsoft.com/visualstudio/extensibility/devenv-command-line-switches-for-vspackage-development).  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Разработчики могут автоматизировать задачи из командной строки, при выполнении devenv.exe, файл, который запускает среду разработки Visual Studio (IDE).  
  
 Следующие задачи.  
  
-   Развертывание приложений в готовые конфигурации от вне интегрированной среды разработки.  
  
-   Автоматически построение проектов, используя конфигурацию параметры сборки или конфигураций отладки.  
  
-   Загрузка IDE в определенных конфигураций из вне интегрированной среды разработки. Кроме того можно настроить при запуске интегрированной среды разработки.  
  
## <a name="guidelines-for-switches"></a>Рекомендации для коммутаторов  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] документация описывает параметры командной строки devenv уровня пользователя. Дополнительные сведения см. в разделе [командной строки devenv](../ide/reference/devenv-command-line-switches.md). Devenv также поддерживает дополнительные параметры командной строки, которые можно использовать с VSPackage разработки, развертывания и отладки.  
  
|Параметр командной строки|Описание|  
|--------------------------|-----------------|  
|/SafeMode|Запускает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в безопасном режиме, загружая только по умолчанию интегрированная среда разработки и служб. /Safemode предотвращает всех пакетов VSPackage сторонних при загрузке [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запускается, обеспечивая надежность работы.<br /><br /> У этого параметра нет аргументов.|  
|/ resetskippkgs|Очищает все пропустить параметры загрузки, добавленные пользователями, желающими исключить загрузку проблемных пакетов VSPackage, затем запускает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Наличие тега SkipLoading отключает загрузку пакета VSPackage. Удаление этого тега снова включает загрузку пакета VSPackage.<br /><br /> У этого параметра нет аргументов.|  
|/ rootsuffix|Запускает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с помощью альтернативное расположение. Следующая команда служит ярлыком, созданные [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] установщика:<br /><br /> devenv/rootsuffix exp<br /><br /> В этом случае exp определяет расположение с определенным расширением, например 10.0Exp вместо версии 10.0. Экспериментальный экземпляр позволяет отлаживать VSPackage отдельно от экземпляра [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] что вы используете для написания кода.<br /><br /> Этот параметр может занять любая строка, которая определяет расположение, которое вы создали с помощью VSRegEx.exe. Дополнительные сведения см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).|  
|/Splash|Показывает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] экран-заставка, как обычно и затем отображает окно сообщения перед отображением основной интегрированной среды разработки. Окно сообщения позволяет изучить экрана-заставки, проверяемый на возможность продукта значок в виде пакета VSPackage, например.<br /><br /> У этого параметра нет аргументов.|  
  
## <a name="see-also"></a>См. также  
 [Добавление параметров командной строки](../extensibility/adding-command-line-switches.md)   
 [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md)

