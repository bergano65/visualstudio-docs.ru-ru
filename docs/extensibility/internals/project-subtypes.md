---
title: Подтипы проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c2e5151131efdab36a3c9e5cf646b1ca9bf94b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922721"
---
# <a name="project-subtypes"></a>Подтипы проектов
Подтипов проекта позволяют настраивать или flavor поведение системы проектов из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Настройки включают сохранение дополнительных данных в файле проекта, добавляя или фильтруя элементы в **Добавление нового элемента** » диалогового окна «Управление как сборки, отладки и развертывания и расширение проекта **свойство Страницы** диалоговое окно. Пакеты VSPackage реализовывать подтипов проекта, с помощью COM статистической обработки.  
  
> [!NOTE]
>  Система проектов Visual C++ не поддерживает подтипов проекта. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] подтипов проекта самой используются для реализации проектов для смарт-устройств и SQL Server.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)  
 Описывает основные концепции подтипов проекта.  
  
 [Инициализация последовательности подтипов проекта](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Описывает последовательность инициализации подтип программный проект с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды.  
  
 [Свойства и методы, расширенные подтипами проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Содержит подробное описание функций и методов, наиболее часто расширены с помощью подтипов проекта.  
  
 [Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Описываются способы сохранения данных в файл проекта и как использовать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для хранения данных в файле проекта через уровни статистических обработок подтип проекта.  
  
 [Пользовательский интерфейс свойств проекта](../../extensibility/internals/project-property-user-interface.md)  
 Описывает, каким образом подтипов проекта можно изменить проект **страницы свойств** диалоговое окно.  
  
 [Расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Сведения о том, как подтипов проекта расширители автоматизации можно использовать для расширения объектной модели автоматизации.  
  
 [Добавление элементов в диалоговое окно "Добавление новых элементов"](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Описывается, как добавить элементы в **Добавление нового элемента** диалоговое окно.  
  
 [Сохранение данных в файлах проектов](../../extensibility/saving-data-in-project-files.md)  
 Объясняет, как подтипом проекта можно сохранить и извлечь подтипа данных в файле проекта с помощью Managed Package Framework (MPF).  
  
 [Обработка специализированного развертывания](../../extensibility/internals/handling-specialized-deployment.md)  
 Объясняет, как подтипов проекта можно указать поведение специализированного развертывания путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейс.  
  
 [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)  
 Описывает добавление и удаление страниц свойств в конструкторе проектов.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Содержит ссылки на разделы с подробным описанием [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проектов.