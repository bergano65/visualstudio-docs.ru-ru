---
title: Параметры командной строки devenv для разработки VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185281"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Параметры командной строки для команды devenv для разработки VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет разработчикам автоматизировать задачи из командной строки при выполнении devenv.exe — файла, запускающего интегрированную среду разработки (IDE) Visual Studio.  
  
 Задачи включают:  
  
- Развертывание приложений в предконструированных конфигурациях извне интегрированной среды разработки.  
  
- Автоматическое построение проектов с использованием предустановленных параметров сборки или конфигураций отладки.  
  
- Загрузка интегрированной среды разработки в конкретных конфигурациях, которые выходят за пределы интегрированной среды разработки. Кроме того, можно настроить интегрированную среду разработки при запуске.  
  
## <a name="guidelines-for-switches"></a>Рекомендации для параметров  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] документация описывает параметры командной строки команды devenv на уровне пользователя. Дополнительные сведения см. в разделе [Параметры командной строки devenv](../ide/reference/devenv-command-line-switches.md). Команда devenv также поддерживает дополнительные параметры командной строки, которые полезны при разработке, развертывании и отладке VSPackage.  
  
|Параметр командной строки|Описание|  
|--------------------------|-----------------|  
|/SafeMode|Запускается [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в защищенном режиме, загружая только интегрированную среду разработки и службы по умолчанию. Параметр/SafeMode предотвращает загрузку пакетов VSPackage сторонних производителей при [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запуске, обеспечивая стабильное выполнение.<br /><br /> У этого параметра нет аргументов.|  
|/resetskippkgs|Очищает все параметры пропускной загрузки, добавленные пользователями, желающими избежать загрузки проблемных пакетов VSPackage, а затем запускает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Наличие тега SkipLoading отключает загрузку VSPackage. Очистка тега повторно включает загрузку VSPackage.<br /><br /> У этого параметра нет аргументов.|  
|/рутсуффикс|Начинается с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] использования альтернативного расположения. Следующая команда выполняется с помощью ярлыка, созданного [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] установщиком:<br /><br /> devenv/Рутсуффикс exp<br /><br /> В этом случае exp определяет расположение с определенным суффиксом, например 10.0 exp, а не 10,0. Экспериментальный экземпляр позволяет выполнять отладку VSPackage отдельно от экземпляра [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , который используется для написания кода.<br /><br /> Этот параметр может принимать любую строку, определяющую расположение, созданное с помощью VSRegEx.exe. Дополнительные сведения см. [в статье экспериментальный экземпляр](../extensibility/the-experimental-instance.md).|  
|/сплаш|Отображает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] экран-заставку как обычно, а затем отображает окно сообщения перед отображением основной интегрированной среды разработки. Окно сообщения позволяет изучить экран-заставку, например, для проверки значка продукта VSPackage.<br /><br /> У этого параметра нет аргументов.|  
  
## <a name="see-also"></a>См. также:  
 [Добавление параметров командной строки](../extensibility/adding-command-line-switches.md)   
 [Параметры командной строки для команды devenv](../ide/reference/devenv-command-line-switches.md)
