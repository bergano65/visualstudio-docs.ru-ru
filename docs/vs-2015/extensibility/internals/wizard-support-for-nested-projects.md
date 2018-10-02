---
title: Поддержка мастера для вложенных проектов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4621627faae761bfe63b7fd056427a3771d21582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571658"
---
# <a name="wizard-support-for-nested-projects"></a>Поддержка мастера для вложенных проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [поддержка мастера для вложенных проектов](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-support-for-nested-projects).  
  
Интегрированная среда разработки выполняет два мастера, которые можно реализовать в родительский проект для вложенных проектов: **новый проект** мастера и **Добавление элемента** мастера.  
  
 Если пользователь запускает **новый проект** мастера, выбрав **добавить проект** и щелкнув **новый проект** в меню "файл" или выбрав **добавить** и щелкните правой кнопкой мыши **новый проект** в обозревателе решений в IDE выполняется **AddProject** команда и реализация в родительский проект **AddProject**команда возвращает либо файл шаблона проекта или файл мастера (VSZ), содержащий набор параметров контекста.  
  
 Точно так же родительском проекте реализации **AddItem** мастеров возвращает VSZ-файл, который имеет отдельный набор параметров контекста.  
  
 Дополнительные сведения о мастерах см. в разделе [мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md), [параметры контекста](../../extensibility/internals/context-parameters.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)

