---
title: Добавление шаблонов проектов и элементов проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203860"
---
# <a name="adding-project-and-project-item-templates"></a>Добавление проекта и шаблонов элементов проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При создании собственных типов проектов необходимо обеспечить поддержку добавления новых проектов и элементов проектов с помощью стандартных [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] диалоговых окон интегрированной среды разработки (IDE). В следующих разделах рассматриваются различные методы добавления проектов и элементов проектов.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Контекст проекта](../../extensibility/internals/project-context.md)  
 Объясняет, что проект предоставляет большую часть контекстных сведений о том, что происходит в среде.  
  
 [Приоритет проекта](../../extensibility/internals/project-priority.md)  
 Объясняется, что элемент проекта обычно является членом одного проекта, чтобы избежать неоднозначности в том, какой проект используется для открытия элемента.  
  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)  
 Предоставляет сведения о двух типах редакторов, которые можно использовать для открытия файлов в проекте, и роль, которую играет проект при определении того, какой редактор следует использовать при открытии элемента проекта.  
  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)  
 Объясняет, что происходит при [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] создании проекта.  
  
 [Добавление элементов в диалоговые окна "Добавить новый элемент"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Описание процесса добавления элементов в диалоговое окно " **Добавление нового элемента** ".  
  
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Содержит пример регистрации нового каталога, содержащего пользовательские шаблоны, доступные в VSPackage.  
  
 [Добавление каталогов в диалоговое окно "Добавить новый элемент"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Содержит пример регистрации нового набора каталогов для диалогового окна **Добавление нового элемента** .  
  
 [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Список различных типов командных элементов, используемых для расширения систем проектов.  
  
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Список CATID для объектов, используемых для расширения [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] систем проектов, и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
## <a name="related-sections"></a>См. также  
 [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции по открытию элемента, привязанного к конкретному редактору для проекта.  
  
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции по открытию стандартного редактора.  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 Содержит ссылки на основные разделы о подтипах проектов. Подтипы проектов расширяют существующие [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] проекты и.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на дополнительные разделы, в которых содержатся сведения о проектировании новых типов проектов.
