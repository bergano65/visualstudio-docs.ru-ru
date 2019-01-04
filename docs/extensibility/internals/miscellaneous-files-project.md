---
title: Проект прочих файлов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 281213751cb25a05e8298ee35ba43453d48ed250
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853113"
---
# <a name="miscellaneous-files-project"></a>Проект прочих файлов
При открытии элементов проекта, интегрированная среда разработки присваивает проекта прочих файлов любые элементы, которые не являются членами всех проектов в решении.  
  
 Проекты играют важную роль при определении того, какой редактор используется в том случае, когда пользователь открывает элемент проекта. Проект может разрабатываться для открытия определенных файлов с помощью редактора определенного проекта или стандартного редактора.  
  
 Проектный редактор обычно требует, что пользователь иметь специальные сведения или использовать специальные интерфейсы из проекта. Дополнительные сведения см. в разделе [Как Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Стандартный редактор можно открыть любой файл конкретного расширения в любом проекте. Пользователь может настраивать некоторые стандартные редакторы, такие как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] текстовый редактор для проектов, но по-прежнему сохранить их общедоступных символов. Стандартные редакторы создаются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод.  
  
 Если проект в решении не отвечает, что он может открывать элемент проекта, интегрированная среда разработки предоставляет специальные проект с именем проекта прочих файлов, который открывает любой файл.  
  
 Для открытия файла вне контекста проекта предоставляет конкретного проекта. Во время обработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> метода проекта прочих файлов всегда отвечает с очень низким приоритетом. Таким образом прочие файлы проекта всегда уступает проекты более высокий приоритет, можно открыть файлы.  
  
 Проект прочих файлов не требуется пользователь явным образом создать его с **новый проект** диалоговое окно. Кроме того проект прочих файлов не поддерживает управление окончательно список элементов проекта. Он использует дополнительный компонент для записи списка последних использованных файлов для каждого пользователя.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)   
 [Практическое руководство. Стандартные редакторы](../../extensibility/how-to-open-standard-editors.md)   
 [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)