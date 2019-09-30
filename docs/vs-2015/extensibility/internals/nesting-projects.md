---
title: Вложенные проекты | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "68180410"
---
# <a name="nesting-projects"></a>Проекты вложения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Разработчики корпоративных приложений, использующие пакет VS, могут группировать схожие типы проектов вместе [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с помощью *вложений проектов*. Например, проект корпоративного шаблона использует вложенные проекты для группировки проектов по категориям. Проекты Business фасадной, проекты пользовательского веб-интерфейса и т. д. группируются в одной категории.  
  
 В этом сценарии нет ограничений на количество проектов, которые разработчик может вкладывать в каждый родительский проект, хотя разработчик может программно предоставлять ограничения. Этот тип группирования можно также сделать рекурсивным. в этом случае проекты того же типа, что и дочерний проект, могут быть вложены в дочерний проект дочернего проекта, который является подпроектом родительского.  
  
 Вложенность проектов не является встроенной частью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Необходимо написать код для включения вложенности и вложенных проектов в дочерних проектах. Родительский проект — это особый пакет VSPackage или тип проекта, созданный и зарегистрированный с собственным идентификатором GUID, включающий код, необходимый для реализации вложенности проекта.  
  
 Пример вложенных проектов можно найти в C# примере вложенного проекта Sample.  
  
## <a name="nested-projects-example"></a>Пример вложенных проектов  
 ![Решение вложенных проектов](../../extensibility/internals/media/vsnestedprojects.gif "вснестедпрожектс")  
Пример вложенных проектов  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Реализация вложенных проектов](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Параметры контекста](../../extensibility/internals/context-parameters.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)
