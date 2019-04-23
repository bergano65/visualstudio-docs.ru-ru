---
title: Расширение панели элементов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: 54026b770a0de7780e950a3e30e649cb67ce1d3b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088708"
---
# <a name="extending-the-toolbox"></a>Расширение панели элементов
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Панель элементов** представляет коллекцию объектов, которые предоставляют функциональные возможности в редакторах и конструкторах через механизм перетаскивания IDE.  
  
 Существует два основных способа, которыми VSPackage работает с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **панелью элементов**.  
  
- VSPackage может добавлять в **панель элементов**новые элементы данных и элементы управления.  
  
- VSPackage может быть целевым объектом или потребителем существующих функциональных возможностей **панели элементов** с поддержкой операций перетаскивания и настройки внешнего вида **панели элементов**.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Практическое руководство. Создание элемента управления панели элементов, использующего Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Описывается создание элемента управления "Панель элементов" с помощью шаблона элемента управления панели элементов Windows Forms.  
  
 [Создание элемента управления панели элементов WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Описывается создание элемента управления "Панель элементов" с помощью шаблона элемента управления панели элементов WPF.  
  
 [Управление панелью элементов](../misc/managing-the-toolbox.md)  
 Описывается, как VSPackage может управлять содержимым и внешним видом **панели элементов**.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Практическое руководство. Управление окном панели элементов](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Описывается, как работать с **панелью элементов** в интегрированной среде разработки (IDE) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Практическое руководство. Элемент управления панели элементов](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Описывается, как управлять **панелью элементов** с помощью модели программирования автоматизации.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Объясняется использование служб [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].