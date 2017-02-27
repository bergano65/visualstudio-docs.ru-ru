---
title: "Выбор между VSPackages общих и управление версиями | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SxS"
  - "Установка Side-by-side"
  - "Установка [Visual Studio SDK] side-by-side"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Выбор между VSPackages общих и управление версиями
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Разные версии Visual Studio могут сосуществовать на одном компьютере. Пакеты VSPackage может поддерживать любое сочетание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] версии.  
  
 Можно включить side\-by\-side установок VSPackages одним из двух стратегий, общий стратегию или версии. Как разместить наличие нескольких версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и соответствующие версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 В общей стратегии один VSPackage регистрируется для использования в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В версии стратегии установки нескольких библиотек VSPackage, один для каждой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] которые поддерживаются.  
  
## Общие пакеты VSPackage  
 С помощью общего VSPackage подходит при использовании нескольких версий одной VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для реализации общих VSPackage, необходимо выполнить следующие действия:  
  
-   Обеспечить совместимость с несколькими версиями VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Таким образом, доступны два способа выполнения задачи:  
  
    -   Ограничить VSPackage с помощью возможности самую раннюю версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] которые поддерживаются.  
  
    -   VSPackage адаптироваться к версии программы [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в которой он выполняется. В случае сбоя запросов для новых служб VSPackage может предложить другие службы, которые поддерживаются в более старых версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Регистрация VSPackage соответствующим образом. Дополнительные сведения см. в разделах [Регистрация VSPackage](../extensibility/internals/vspackage-registration.md) и [Managed VSPackage Registration](http://msdn.microsoft.com/ru-ru/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Регистрация расширений файлов соответствующим образом. Для получения дополнительной информации см. [Регистрация расширений файлов для развертываний Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Создать установщик, который развертывает VSPackage для соответствующих версий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделах [Установка пакетов VSPackages с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) и [Компонент управления](../extensibility/internals/component-management.md).  
  
-   Решить проблему регистрации конфликтов. Для получения дополнительной информации см. [Регистрация VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Убедитесь, что файлы как общий, так и с версией учитывают подсчет ссылок, чтобы разрешить безопасный установки и удаления нескольких версий. Дополнительные сведения см. в разделе [Компонент управления](../extensibility/internals/component-management.md).  
  
## Управление версиями пакеты VSPackage  
 В версии стратегии VSPackage, создайте один VSPackage для каждой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] которые поддерживаются. Это удобно, если вы хотите воспользоваться преимуществами служб, предоставляемых в более поздних версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], так как каждый VSPackage могут изменяться без влияния на другие. Тем не менее с версией стратегии создания нескольких двоичных файлов с единой базой кода или из нескольких базовых классов независимый код, может требовать дополнительные начальной разработки, чем общей стратегии. Кроме того, дополнительная настройка работы может потребоваться потому, что необходимо создать отдельные настройки для каждой версии либо одной программы установки, которая определяет версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] устанавливаемые и поддерживает VSPackage.  
  
## Двоичная совместимость  
 Как правило двоичные совместимости позволяет VSPackages машинного кода, разработанных с помощью более ранних версий Visual Studio для выполнения в более поздних версиях Visual Studio. Тем не менее существует три важных исключения:  
  
-   Если VSPackage зависит от определенной версии среды CLR, то необходимо определить, в какой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] его выполнения.  
  
-   VSPackage может зависят от определенных функций другой VSPackage или другого продукта. Следовательно VSPackage можно запустить только когда удовлетворяются зависимость.  
  
-   VSPackage могут влиять на исправление безопасности в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пакета обновления или более поздней версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В таких случаях VSPackage, разработанные с использованием более ранней версии [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] могут не работать в версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] после применения исправления безопасности. Однако можно пакет с более поздней версии и также запустить его в более ранних версиях.  
  
 Управляемых пакетов VSPackages должны быть построены с помощью версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] соответствует целевой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Вдобавок к планированию для совместимости с двоичными данными для двоичных файлов VSPackage, вам также следует рассмотреть возможность решения и проекта форматы файлов. Если VSPackage создает новый тип проекта, необходимо решить, ли его можно запустить только одну версию или в нескольких версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для получения дополнительной информации см. [Обновление пользовательских проектов](../misc/upgrading-custom-projects.md).  
  
## См. также  
 [Установка пакетов VSPackages с помощью установщика Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Компонент управления](../extensibility/internals/component-management.md)