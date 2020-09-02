---
title: Проект прочих файлов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179787"
---
# <a name="miscellaneous-files-project"></a>Проект прочих файлов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Когда пользователь открывает элементы проекта, интегрированная среда разработки присваивает проекту Прочие файлы все элементы, которые не являются членами каких-либо проектов в решении.  
  
 Проекты играют важную роль в определении того, какой редактор используется, когда пользователь открывает элемент проекта. Проект может быть разработан для открытия определенных файлов с помощью редактора конкретного проекта или стандартного редактора.  
  
 Для конкретного проекта обычно требуется, чтобы пользователь имел специальные знания или использовал специальные интерфейсы из проекта. Дополнительные сведения см. [в разделе руководство. открытие редакторов, зависящих от проекта](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Стандартный редактор может открыть любой файл определенного расширения в любом проекте. Пользователь может настроить некоторые стандартные редакторы, например [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] текстовый редактор, для проектов, но сохранили свои открытые символы. Стандартные редакторы создаются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метода.  
  
 Если ни один из проектов в решении не реагирует на то, что он может открыть элемент проекта, интегрированная среда разработки предоставляет специальный проект с именем "Прочие файлы", который открывает любой файл.  
  
 Этот специальный проект предоставляет для открытия файла вне контекста проекта. Во время обработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> метода проект прочих файлов всегда отвечает с очень низким приоритетом. Таким образом, проект "Прочие файлы" всегда возвращает любой проект с более высоким приоритетом, который может открывать файлы.  
  
 В проекте "Прочие файлы" пользователь не должен явно создавать его с помощью диалогового окна " **Новый проект** ". Кроме того, проект прочих файлов не будет постоянно управлять списком членов проекта. Он использует необязательный компонент для записи списка последних использованных файлов для каждого пользователя.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Пошаговое руководство. открытие редакторов, зависящих от проекта](../../extensibility/how-to-open-project-specific-editors.md)   
 [Руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)   
 [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
