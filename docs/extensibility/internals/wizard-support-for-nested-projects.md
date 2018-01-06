---
title: "Поддержка мастера для вложенных проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757968aabfc256cda37a103d48c8d12f1fc16fa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
Интегрированная среда разработки запускает два мастера, которые можно реализовать родительский проект для вложенных проектов: **новый проект** мастера и **добавить элемент** мастера.  
  
 Если пользователь запускает **новый проект** мастера, выбрав **добавить проект** и щелкнув **новый проект** меню файл или выбрав **добавить** и щелкните правой кнопкой мыши **новый проект** в обозревателе решений в IDE выполняется **AddProject** команда и реализация родительский проект **AddProject**команда возвращает либо файл шаблона проекта или файла мастера (VSZ) с набором параметров контекста.  
  
 Аналогичным образом, родительский проект реализация **AddItem** VSZ-файл, который имеет разный набор параметров контекста, возвращает мастеров.  
  
 Дополнительные сведения о мастерах см. в разделе [мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md), [параметры контекста](../../extensibility/internals/context-parameters.md) и [регистрации шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)