---
title: Выбор между общих и с контролем версий пакетов VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 62033dc78e5595cefdf4f3ae39a95e68c64b9ee4
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283227"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Выбор между общих и с контролем версий пакетов VSPackage
Разные версии Visual Studio могут сосуществовать на одном компьютере. Пакеты VSPackage может поддерживать любое сочетание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] версий.  
  
 Вы можете включить side-by-side установки пакетов VSPackage, одним из двух стратегий, общий стратегию или с контролем версий. Оба вместить наличие нескольких версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и связанных версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 В общей стратегии, один пакет VSPackage зарегистрирован для использования в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В стратегии с версиями, устанавливаются несколько библиотек DLL VSPackage, один для каждой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которую поддерживаете.  
  
## <a name="shared-vspackages"></a>Общие пакеты VSPackage  
 С помощью общего VSPackage подходит при использовании же VSPackage в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Чтобы реализовать общий VSPackage, выполните следующие действия.  
  
-   Обеспечить совместимость с несколькими версиями VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Оба способа выполнения задачи таким образом доступны:  
  
    -   Ограничить VSPackage с помощью только за компонентами самую раннюю версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , вы поддерживаете.  
  
    -   Программирование VSPackage для адаптации к версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в котором он выполняется. При сбое запросов для новых служб VSPackage может предложить другие службы, которые поддерживаются в более старых версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Регистрация VSPackage соответствующим образом. Дополнительные сведения см. в разделе [регистрации VSPackage](../extensibility/internals/vspackage-registration.md) и [регистрации управляемого VSPackage](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Регистрация расширений файлов соответствующим образом. Дополнительные сведения см. в разделе [Регистрация расширений имен файлов для развертываний side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Создать установщик, который развертывает VSPackage для соответствующих версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) и [Управление компонентами](../extensibility/internals/component-management.md).  
  
-   Решить проблему регистрации конфликтов. Дополнительные сведения см. в разделе [регистрации VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Убедитесь, что файлы как общих, так и с контролем версий учитывают подсчет ссылок, чтобы разрешить безопасный установки и удаления нескольких версий. Дополнительные сведения см. в разделе [Управление компонентами](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Управление версиями пакетов VSPackage  
 В разделе с версиями стратегии VSPackage, создайте один VSPackage для каждой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которую поддерживаете. Это удобно, если вы планируете использовать преимущества службы, предоставляемые более поздних версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], так как для каждого пакета VSPackage может развиваться, не затрагивая остальные. Тем не менее с версиями стратегии с созданием несколько двоичных файлов, из единой базой кода или из нескольких независимых баз кода, может требовать дополнительные начальной разработки, чем общей стратегии. Кроме того, работа по дополнительной настройке могут быть необходимы, так как необходимо создать отдельные настройки для каждой версии либо единую программу установки, который определяет версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , устанавливаемые и поддерживает VSPackage.  
  
## <a name="binary-compatibility"></a>Совместимость двоичных файлов  
 Как правило двоичная совместимость позволяет машинного кода пакеты VSPackage, разработанные в более ранних версиях Visual Studio для выполнения в более поздних версиях Visual Studio. Тем не менее существует три важных исключения:  
  
-   Если VSPackage зависит от конкретной версии среда CLR, то он должен определить, в какой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] он выполняется.  
  
-   VSPackage может зависеть от над конкретной возможностью другом пакете VSPackage или другого продукта. Следовательно VSPackage можно запускать, только когда удовлетворяется зависимость.  
  
-   VSPackage может повлиять исправление безопасности в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пакета обновления или более поздней версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В таком случае VSPackage, разработанные с использованием более ранней версии [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] могут не работать в версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] применили исправление безопасности. Тем не менее можно пакет с более поздней версии и также запустить его в более ранних версий.  
  
 Управляемые пакеты VSPackage должны быть построены с помощью версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] , совпадает с целевой версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Вдобавок к планированию для двоичной совместимости для вашего VSPackage двоичных файлов, вам также следует рассмотреть возможность решения и проекта форматов файлов. Если VSPackage создает новый тип проекта, необходимо решить, ли его можно запустить только одну версию или в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [обновление пользовательских проектов](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Управление компонентами](../extensibility/internals/component-management.md)