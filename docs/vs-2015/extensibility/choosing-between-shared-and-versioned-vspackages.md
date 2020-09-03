---
title: Выбор между общими и версиями пакетов VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821980"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Выбор между общими пакетами VSPackage и пакетами с контролем версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Разные версии Visual Studio могут сосуществовать на одном компьютере. Пакеты VSPackage могут поддерживать любой набор [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] версий.  
  
 Параллельные установки пакетов VSPackage можно включить с помощью одной из двух стратегий: общей стратегии или стратегии управления версиями. Оба варианта удовлетворяют наличие нескольких версий [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и связанных версий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 В общей стратегии один пакет VSPackage регистрируется для использования в нескольких версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . В стратегии управления версиями устанавливаются несколько библиотек DLL VSPackage, по одной для каждой [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] поддерживаемой версии.  
  
## <a name="shared-vspackages"></a>Общие пакеты VSPackage  
 Использование общего пакета VSPackage подходит при использовании одного пакета VSPackage в нескольких версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Для реализации общего пакета VSPackage необходимо выполнить следующие действия.  
  
- Сделайте пакет VSPackage совместимым с несколькими версиями [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Доступны два способа:  
  
  - Ограничьте пакет VSPackage, используя только возможности самой ранней [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] поддерживаемой версии.  

  - Заполните пакет VSPackage для адаптации к версии, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в которой он выполняется. Затем, если происходит сбой запросов к более новым службам, пакет VSPackage может предлагать другие службы, которые поддерживаются в более ранних версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Зарегистрируйте пакет VSPackage соответствующим образом. Дополнительные сведения см. в статье [Регистрация VSPackage](../extensibility/internals/vspackage-registration.md) и [управляемая регистрация VSPackage](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Зарегистрируйте расширения файлов соответствующим образом. Дополнительные сведения см. в разделе [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Создайте установщик, который развертывает пакет VSPackage для соответствующих версий [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Дополнительные сведения см. [в разделе Установка пакетов VSPackage с помощью установщик Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) и [управления компонентами](../extensibility/internals/component-management.md).  
  
- Устраните проблемы с конфликтами регистрации. Дополнительные сведения см. в разделе [Регистрация VSPackage](../extensibility/internals/vspackage-registration.md).  
  
- Убедитесь, что общие и версии файлов учитывают подсчет ссылок, чтобы обеспечить надежную установку и удаление нескольких версий. Дополнительные сведения см. в разделе [Управление компонентами](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Версии пакетов VSPackage  
 В рамках стратегии VSPackage с контролем версий вы создаете один пакет VSPackage для каждой [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] поддерживаемой версии. Это подходит, если вы планируете использовать службы, предоставляемые более поздними версиями [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , так как каждый пакет VSPackage может развиваться, не затрагивая другие. Тем не менее, стратегия создания нескольких двоичных файлов из одной базы кода или из нескольких независимых баз кода может привести к более начальной разработке, чем общая стратегия. Кроме того, может потребоваться дополнительная работа по установке, поскольку необходимо создать отдельную программу установки для каждой версии или единую программу установки, которая определяет версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , установленные и поддерживаемые пакетом VSPackage.  
  
## <a name="binary-compatibility"></a>Двоичная совместимость  
 Как правило, двоичная совместимость позволяет использовать пакеты VSPackage машинного кода, разработанные в более ранних версиях Visual Studio, в более поздних версиях Visual Studio. Однако есть три важных исключения.  
  
- Если пакет VSPackage использует определенную версию среды CLR, он должен определить, в какой версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] она выполняется.  
  
- Пакет VSPackage может иметь зависимость от определенной функции другого пакета VSPackage или другого продукта. Следовательно, пакет VSPackage может выполняться только в том случае, если зависимость удовлетворена.  
  
- На пакеты VSPackage может повлиять исправление безопасности в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] пакете обновления или более поздней версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . В таких случаях пакет VSPackage, разработанный с более ранней версией, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] может не работать в версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] после применения исправления безопасности. Однако можно перестроить пакет с помощью более поздней версии, а также запустить его в более ранних версиях.  
  
  Управляемые пакеты VSPackage должны быть созданы с использованием версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] , соответствующей целевой версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Помимо планирования двоичной совместимости для двоичных файлов VSPackage, следует также рассмотреть форматы файлов решения и проекта. Если пакет VSPackage создает новый тип проекта, необходимо решить, может ли он работать только в одной версии или в нескольких версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Дополнительные сведения см. в разделе [Обновление пользовательских проектов](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка пакетов VSPackage с помощью установщик Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Управление компонентами](../extensibility/internals/component-management.md)
