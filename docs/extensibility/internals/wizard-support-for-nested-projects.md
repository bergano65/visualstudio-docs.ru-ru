---
title: Поддержка мастера для вложенных проектов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e8a32db2542ae1729a7fdc87cc2ab32845f8ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
Интегрированная среда разработки запускает два мастера, которые можно реализовать родительский проект для вложенных проектов: **новый проект** мастера и **добавить элемент** мастера.  
  
 Если пользователь запускает **новый проект** мастера, выбрав **добавить проект** и щелкнув **новый проект** меню файл или выбрав **добавить** и щелкните правой кнопкой мыши **новый проект** в обозревателе решений в IDE выполняется **AddProject** команда и реализация родительский проект **AddProject**команда возвращает либо файл шаблона проекта или файла мастера (VSZ) с набором параметров контекста.  
  
 Аналогичным образом, родительский проект реализация **AddItem** VSZ-файл, который имеет разный набор параметров контекста, возвращает мастеров.  
  
 Дополнительные сведения о мастерах см. в разделе [мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md), [параметры контекста](../../extensibility/internals/context-parameters.md) и [регистрации шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)