---
title: Подтипы проекта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706412"
---
# <a name="project-subtypes"></a>Подтипы проектов
Подтипы проекта позволяют настроить или приправить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поведение проектных систем. Настройки включают сохранение дополнительных данных в файле проекта, добавление или фильтрацию элементов в диалоговом поле **Add New Item,** контроль за тем, как сборки отлаживаются и развертываются, и расширение диалогового окна **страниц свойств** проекта. VSPackages реализуют подтипы проекта с использованием агрегации COM.

> [!NOTE]
> Система проекта Visual C' не поддерживает подтипы проектов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]сам использует подтипы проектов для реализации проектов S'L Server и Smart Device.

## <a name="in-this-section"></a>В этом разделе
- [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)

 Описывает концепцию подтипов проектов.

- [Инициализация последовательности подтипов проекта](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Описывает программную последовательность инициализации подтипа проекта по окружающей среде. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- [Свойства и методы, расширенные подтипами проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Предоставляет подробное описание функций и методов, наиболее часто расширяемых с помощью подтипов проекта.

- [Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Описывает, как сохранять данные в файле проекта и как использовать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> их для поддержания данных в файле проекта на уровнях агрегации подтипов проекта.

- [Пользовательский интерфейс свойств проекта](../../extensibility/internals/project-property-user-interface.md)

 Описывает, как подтипы проекта могут изменять диалоговую книжку страниц **свойств** проекта.

- [Расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Предоставляет информацию о том, как подтипы проекта могут использовать расширители автоматизации для расширения модели объектов автоматизации.

- [Добавление элементов в диалоговое окно "Добавить новый элемент"](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Описывает, как добавить элементы в диалоговую коробку **Add New Item.**

- [Сохранение данных в файлах проектов](../../extensibility/saving-data-in-project-files.md)

 Объясняет, как подтип проекта может сохранять и извлекать данные, связанные с подтипом, в файле проекта с помощью рамочной программы управляемого пакета (MPF).

- [Обработка специализированного развертывания](../../extensibility/internals/handling-specialized-deployment.md)

 Объясняет, как подтипы проекта могут обеспечить специализированное поведение развертывания путем реализации интерфейса. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>

- [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)

 Описывает добавление и удаление страниц свойств в проекте Designer.

## <a name="related-sections"></a>Связанные разделы
- [Типы проектов](../../extensibility/internals/project-types.md)

 Предоставляет ссылки на [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] темы с подробным описанием проектов.
