---
title: Управление пакетами VSPackage | Документация Майкрософт
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
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 349dc380e23e5f76ad32631384bc4db8fceeff00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568579"
---
# <a name="managing-vspackages"></a>Управление пакетами VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [пакеты VSPackage, управление](https://docs.microsoft.com/visualstudio/extensibility/managing-vspackages).  
  
В большинстве случаев не нужно беспокоиться об управлении пакеты VSPackage, так как шаблоны проектов и элементов, зарегистрировать и автоматически загрузить пакет. Однако в некоторых случаях может потребоваться узнать чуть подробнее для пакета управления.  
  
## <a name="using-the-experimental-instance"></a>С помощью экспериментальный экземпляр  
 Чтобы узнать больше о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Регистрация и отмена регистрации пакетов VSPackage  
 Чтобы узнать о регистрации и отмены регистрации пакетов VSPackage и других типах расширения, см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Загрузка VSPackage  
 Пакеты VSPackage может быть присвоено автозагрузки, когда определенный CMDUICONTEXT GUID включен. Дополнительные сведения см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме  
 Класс AsyncPackage пакет загрузки в фоновом потоке для повышения скорости отклика пользовательского интерфейса в Visual Studio. Дополнительные сведения см. в разделе [как: использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Контекст пользовательского интерфейса на основе правил для расширений  
 Контексты пользовательского интерфейса на основе правил позволяет разработчикам расширений определить точные условия, при которых активируется контекст пользовательского интерфейса и загружаются связанные пакеты VSPackage. Дополнительные сведения см. в разделе [как: контекст пользовательского интерфейса на основе использования правил для расширений Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Устранение неполадок, связанных с пакетами VSPackage  
 Узнайте методы устранения неполадок пакетов VSPackage, не загружаются или при возникновении ошибки: [Устранение неполадок пакетов VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)

