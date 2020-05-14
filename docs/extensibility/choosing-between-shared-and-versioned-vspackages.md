---
title: Выбор между общими и версиями VSPackages (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739887"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Выбирайте между общими и версиями VSPackages
Различные версии Visual Studio могут сосуществовать на одном компьютере. VSPackages может поддерживать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] любое сочетание версий.

 Вы можете включить бок о бок установки VSPackages через любой из двух стратегий, общей стратегии или версии стратегии. Оба учитывают наличие нескольких [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] версий и связанных с ними версий рамочной программы .NET.

 В общей стратегии один VSPackage зарегистрирован для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]использования в нескольких версиях . В стратегии версии установлено несколько DLL VSPackage, по одному для каждой версии, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] которую вы поддерживаете.

## <a name="shared-vspackages"></a>Общие VSPackages
 Использование общего VSPackage является целесообразным, когда вы используете [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]тот же VSPackage в нескольких версиях. Для реализации общего VSPackage необходимо предпринять следующие шаги:

- Сделайте ваш VSPackage совместимым [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]с несколькими версиями. Доступны два способа сделать это:

  - Ограничьте свой VSPackage с использованием только [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] особенностей самой ранней версии, которую вы поддерживаете.

  - Программа VSPackage, чтобы адаптироваться [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] к версии, в которой он работает. Затем, если запросы для новых служб не удается, ваш VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]может предложить другие услуги, которые поддерживаются в старых версиях .

- Зарегистрируйте свой VSPackage надлежащим образом. Для получения дополнительной информации, см [VSPackage регистрации](../extensibility/internals/vspackage-registration.md) и [управляемой регистрации VSPackage](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Зарегистрируйте расширения файлов надлежащим образом. Для получения дополнительной [Registering file name extensions for side-by-side deployments](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)информации см.

- Создайте установщик, который развертывает ваш [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage для соответствующих версий. Для получения дополнительной информации [см. Установка VSPackages с установкой Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) и [управлением компонентами.](../extensibility/internals/component-management.md)

- Решение вопроса о регистрационных коллизиях. Для получения дополнительной информации, см [VSPackage регистрации](../extensibility/internals/vspackage-registration.md).

- Убедитесь, что как общие, так и версионные файлы соблюдали подсчет ссылок, чтобы обеспечить безопасную установку и удаление нескольких версий. Для получения дополнительной информации [см.](../extensibility/internals/component-management.md)

## <a name="versioned-vspackages"></a>Версия VSPackages
 В соответствии со стратегией VSPackage, вы создаете один VSPackage для каждой версии, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] которую вы поддерживаете. Это уместно, когда вы ожидаете воспользоваться [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]услугами, предоставляемыми более поздними версиями, потому что каждый VSPackage может развиваться, не затрагивая других. Тем не менее, версия стратегии создания нескольких бинарных файлов, как из одной базы кода, так и из нескольких независимых баз кода, может повлечь за собой более первоначальную разработку, чем общая стратегия. Кроме того, может потребоваться дополнительная работа по настройке, поскольку необходимо создать либо отдельную [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] настройку для каждой версии, либо одну настройку, которая определяет версии, которые установлены, и что ваш VSPackage поддерживает.

## <a name="binary-compatibility"></a>Совместимость на уровне двоичного кода
 Как правило, двоичная совместимость позволяет родной код VSPackages разработан с более ранними версиями Visual Studio для запуска в более поздних версиях Visual Studio. Однако есть три важных исключения:

- Если ваш VSPackage опирается на определенную версию общего времени выполнения языка, то он должен определить, в какой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] он работает.

- VSPackage может иметь зависимость от конкретной функции другого VSPackage или другого продукта. Следовательно, VSPackage может работать только там, где зависимость удовлетворена.

- VSPackage может быть затронут исправлением безопасности в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]пакете услуг или более поздней версией. В этих случаях VSPackage, разработанный с [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] более ранней [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] версией, может не работать в версиях после применения исправления безопасности. Тем не менее, вы можете восстановить свой пакет с более поздней версией и запустить его в более ранних версиях.

  Управляемые VSPackages должны быть [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] построены [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] с использованием [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]версии и, которые соответствуют целевой версии.

  В дополнение к планированию бинарной совместимости для двоичных файлов VSPackage, вы также должны рассмотреть форматы файлов решения и файла проекта. Если ваш VSPackage создает новый тип проекта, вы должны решить, может [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ли он работать только в одной версии или в нескольких версиях. Для получения дополнительной информации [см.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

## <a name="see-also"></a>См. также
- [Установка VSPackages с установкой Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Управление компонентами](../extensibility/internals/component-management.md)
