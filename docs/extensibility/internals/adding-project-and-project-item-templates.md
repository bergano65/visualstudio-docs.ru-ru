---
title: Добавление проекта и шаблоны элементов проектов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db53ddce3161097347760026aea16a51f8098519
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499638"
---
# <a name="add-project-and-project-item-templates"></a>Добавьте в проект и шаблоны элементов проекта
При создании собственных типов проектов, вы должны предоставить поддержку для добавления новых проектов и элементов проекта с помощью стандарта [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированных диалоговые окна Интегрированной среды разработки. В следующих разделах рассматриваются различные методы для добавления проектов и элементов проектов.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Контекст проекта](../../extensibility/internals/project-context.md)  
 Объясняет, что проект предоставляет основные сведения о контексте для упрощенной среды.  
  
 [Приоритет проекта](../../extensibility/internals/project-priority.md)  
 Объясняет, что элемент проекта обычно является членом одного проекта, чтобы избежать неоднозначности, о том, какие позволяет открыть элемент проекта.  
  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)  
 Сведения об этих двух типах редакторов, которые могут использоваться для открытия файлов в проекте и в роли, проект играет определить, какой редактор использовать при открытии элемента проекта.  
  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)  
 Объясняет, что происходит при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] создается проект.  
  
 [Добавление элементов в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Описание процесса добавления элементов к **Добавление нового элемента** диалоговое окно.  
  
 [Добавить каталоги в диалоговом окне "новый проект" окно](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Предоставляет пример регистрации новый каталог, содержащий пользовательские шаблоны, доступные через VSPackage.  
  
 [Добавить каталоги в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Предоставляет пример новый набор каталогов для регистрации **Добавление нового элемента** диалоговое окно.  
  
 [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Перечислены различные типы элементов команды, используемые для расширения систем проектов.  
  
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Перечисляет идентификаторы CATID для объектов, которые используются для расширения [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] системы проектов.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Как: открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции по открытию элемент само по себе привязан к определенном редакторе для проекта.  
  
 [Как: открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции по открытию стандартного редактора.  
  
 [Подтипов проекта](../../extensibility/internals/project-subtypes.md)  
 Ссылки на концептуальные разделы подтип проекта. Подтипов проекта расширять существующие [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проектов.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на дополнительные разделы, которые содержат сведения о создании новых типов проектов.