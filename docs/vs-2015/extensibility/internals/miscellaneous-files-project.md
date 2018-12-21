---
title: Проект прочих файлов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5786eb21813125237a35ed185542b5f73bdc839
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777894"
---
# <a name="miscellaneous-files-project"></a>Проект прочих файлов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При открытии элементов проекта, интегрированная среда разработки присваивает проекта прочих файлов любые элементы, которые не являются членами всех проектов в решении.  
  
 Проекты играют важную роль при определении того, какой редактор используется в том случае, когда пользователь открывает элемент проекта. Проект может разрабатываться для открытия определенных файлов с помощью редактора определенного проекта или стандартного редактора.  
  
 Проектный редактор обычно требует, что пользователь иметь специальные сведения или использовать специальные интерфейсы из проекта. Дополнительные сведения см. в разделе [как: открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Стандартный редактор можно открыть любой файл конкретного расширения в любом проекте. Пользователь может настраивать некоторые стандартные редакторы, такие как [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] текстовый редактор для проектов, но по-прежнему сохранить их общедоступных символов. Стандартные редакторы создаются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод.  
  
 Если проект в решении не отвечает, что он может открывать элемент проекта, интегрированная среда разработки предоставляет специальные проект с именем проекта прочих файлов, который открывает любой файл.  
  
 Для открытия файла вне контекста проекта предоставляет конкретного проекта. Во время обработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> метода проекта прочих файлов всегда отвечает с очень низким приоритетом. Таким образом прочие файлы проекта всегда уступает проекты более высокий приоритет, можно открыть файлы.  
  
 Проект прочих файлов не требуется пользователь явным образом создать его с **новый проект** диалоговое окно. Кроме того проект прочих файлов не поддерживает управление окончательно список элементов проекта. Он использует дополнительный компонент для записи списка последних использованных файлов для каждого пользователя.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Как: открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)   
 [Как: открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)   
 [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)

