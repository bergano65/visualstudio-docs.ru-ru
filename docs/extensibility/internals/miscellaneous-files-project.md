---
title: "Прочие файлы проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d3fa64b06504d8982594945f5b0c38956676b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="miscellaneous-files-project"></a>Прочие файлы проекта
При открытии элементов проекта, интегрированная среда разработки присваивает проекта прочих файлов любые элементы, которые не являются членами все проекты в решении.  
  
 Проекты играют важную роль при определении того, какой редактор используется в том случае, когда пользователь открывает элемент проекта. Проект может разрабатываться открывать определенные файлы с помощью редактора для конкретного проекта или стандартного редактора.  
  
 Редактор для конкретного проекта обычно требует, что пользователя требуются специальные знания, или использовать специальные интерфейсы из проекта. Дополнительные сведения см. в разделе [как: открытие редакторов конкретного проекта](../../extensibility/how-to-open-project-specific-editors.md).  
  
 В любом проекте стандартного редактора можно открыть любой файл определенное расширение. Пользователь может настроить некоторые стандартные редакторы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] текстовый редактор для проектов, но по-прежнему хранить их открытых символов. Стандартные редакторы создаются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод.  
  
 Если проект в решении не отвечает, его можно открыть элемент проекта, интегрированная среда разработки предоставляет специальные проект с названием проекта прочих файлов, открывает любого файла.  
  
 Для открытия файла вне контекста проекта предоставляет конкретного проекта. Во время обработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> метода проекта прочих файлов всегда отвечает с очень низким приоритетом. Таким образом прочие файлы проектов всегда дает в любой проект более высокий приоритет, можно открыть файлы.  
  
 Прочие файлы проектов не пользователю необходимо явно создать его с **новый проект** диалоговое окно. Кроме того проекта прочих файлов не поддерживает управление окончательно список элементов проекта. Он использует это дополнительный компонент для записи список недавно использованных файлов для каждого пользователя.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Как: открытие редакторов конкретного проекта](../../extensibility/how-to-open-project-specific-editors.md)   
 [Как: открытие редакторов Standard](../../extensibility/how-to-open-standard-editors.md)   
 [Добавление в проект и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)