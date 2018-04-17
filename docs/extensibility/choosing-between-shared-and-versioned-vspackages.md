---
title: Выбор между общих и с версией пакетов VSPackage | Документы Microsoft
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
ms.openlocfilehash: ce7f58d664c6a186146272af16324be2fee90983
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Выбор между общих и с версией пакетов VSPackage
Разные версии Visual Studio могут сосуществовать на одном компьютере. Пакеты VSPackage может поддерживать любое сочетание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] версии.  
  
 Вы можете включить-параллельная установка пакетов VSPackage, одним из двух стратегий, общей стратегии или с версиями стратегии. Как разместить наличие нескольких версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и связанных версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 В общей стратегии один VSPackage регистрируется для использования в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Стратегии, с версиями, устанавливаются несколько библиотек DLL VSPackage, один для каждой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которые поддерживаются.  
  
## <a name="shared-vspackages"></a>Общие пакеты VSPackage  
 С помощью общего VSPackage подходит при использовании того же пакета VSPackage в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для реализации общей VSPackage, необходимо выполнить следующие действия:  
  
-   Сделать VSPackage, совместимым с несколькими версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Два способа сделать так доступны:  
  
    -   Ограничить VSPackage с помощью функции самую раннюю версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которые поддерживаются.  
  
    -   Программирование VSPackage для адаптации к версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , в котором он выполняется. При сбое запросов для новых служб VSPackage могут предложить другие службы, которые поддерживаются в более старых версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Зарегистрируйте VSPackage соответствующим образом. Дополнительные сведения см. в разделе [регистрации VSPackage](../extensibility/internals/vspackage-registration.md) и [регистрации управляемого VSPackage](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Регистрация расширений файлов соответствующим образом. Дополнительные сведения см. в разделе [регистрации расширения имен файлов для развертываний Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Создать программу установки, которая развертывает VSPackage для соответствующих версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) и [управления компонентами](../extensibility/internals/component-management.md).  
  
-   Решить проблему регистрации конфликтов. Дополнительные сведения см. в разделе [регистрации VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Убедитесь, что общих и версиями файлов следовать подсчет ссылок, чтобы разрешить безопасное установки и удаления нескольких версий. Дополнительные сведения см. в разделе [управления компонентами](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>С версиями пакетов VSPackage  
 В версии стратегии VSPackage, создайте один пакет VSPackage для каждой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которые поддерживаются. Это удобно, если предполагается, чтобы воспользоваться преимуществами служб, предоставляемых в более поздних версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], так как для каждого пакета VSPackage могут изменяться без влияния на другие. Тем не менее с версиями стратегия создания нескольких двоичных файлов, из единой базой кода или из нескольких базовых классов независимый код, может требовать дополнительных начальной разработки, чем общей стратегии. Кроме того, дополнительная настройка рабочих может требоваться потому, что необходимо создать отдельные программы установки для каждой версии либо единой программы установки, который определяет версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , устанавливаемые и поддерживает VSPackage.  
  
## <a name="binary-compatibility"></a>Двоичная совместимость  
 Как правило совместимости с двоичными данными позволяет пакеты VSPackage машинного кода, разработанных с помощью более ранних версиях Visual Studio для выполнения в более поздних версиях Visual Studio. Тем не менее есть три важных исключения:  
  
-   Если VSPackage зависит от конкретной версии среды CLR, то он должен определить, в какой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] его выполнения.  
  
-   VSPackage может с зависимостями от другой VSPackage или другом продукте для определенного компонента. Следовательно пакет VSPackage можно запустить только которой будет настроена.  
  
-   VSPackage могут быть затронуты исправление безопасности в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пакета обновления или более поздней версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В таких случаях VSPackage, разработанные с более ранней версии [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] могут не работать в версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] применения исправления безопасности. Тем не менее можно перестроить пакет с более поздней версии и также запустить его в более ранних версиях.  
  
 Управляемые пакеты VSPackage должны быть построены с помощью версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] , соответствует версии целевого [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Помимо планирование совместимости с двоичными данными для двоичных файлов VSPackage, вы также следует рассмотреть возможность решения и проекта форматы файлов. Если VSPackage создает новый тип проекта, необходимо решить, ли его можно запустить только одной версии или в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [обновление пользовательских проектов](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Управление компонентами](../extensibility/internals/component-management.md)