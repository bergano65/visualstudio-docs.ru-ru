---
title: "Проекты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>Проекты
В Visual Studio, проекты — это контейнеры, которые разработчики используют для организации файлов исходного кода и других ресурсов, которые отображаются в **обозревателе решений**. Как правило проекты, файлы (например, файл .csproj для проекта C#), хранятся ссылки на файлы исходного кода и ресурсов, таких как файлы растровых изображений. Проекты позволяют организовывать, создавать, отлаживать и развертывать исходный код, ссылки на веб-служб и баз данных и другие ресурсы. Пакеты VSPackage можно расширить систему проекта Visual Studio благодаря трем основным факторам: *типы проектов*, *проекта подтипы*, и *пользовательские средства*.  
  
## <a name="in-this-section"></a>Содержание  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 *Типы проектов* добавить поддержку новых типов проектов, например языков программирования. Например каждый язык, поддерживающий Visual Studio имеет собственный тип проекта и пример интеграции IronPython включает тип проекта для языка IronPython. Необходимо создать тип проекта для языков, отличных от C# или Visual Basic для настройки как элементы построения, отладки, развертывания и отображается в **обозревателе решений**. Дополнительные сведения см. в разделе [типы проектов](../../extensibility/internals/project-types.md).  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 *Проект подтипы* основаны на типах проектов и может использоваться для настройки способа построения, отладки и развертывания проектов. Visual Studio использует проект подтипы проектов смарт-устройств; они настройки развертывания путем копирования вновь созданных программы с компьютера разработчика на целевом устройстве. C# и типы проектов Visual Basic можно использовать как основу для проекта подтипов. Типы проектов C++ невозможно. Собственные типы проектов можно также используется как основа для проекта подтипы. Дополнительные сведения см. в разделе [подтипы проекта](../../extensibility/internals/project-subtypes.md).  
  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Описание веб-проект, который в свою очередь создавать веб-приложения.  
  
 [Создание нового проекта: За кулисами, часть&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) и [Создание нового проекта: за кулисами, часть&2;](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Объясняется, что происходит при создании нового проекта.  
  
 [Примеры VSSDK](../../misc/vssdk-samples.md)  
 Описание образцов VSSDK, которые работают с проектами и решениями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [В Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Объясните различные аспекты расширяемости Visual Studio.
