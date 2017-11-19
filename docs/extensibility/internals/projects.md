---
title: "Проекты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: "43"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c175d85b55734df841f30d131639c3bfeed40361
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="projects"></a>Проекты
В Visual Studio проекты — это контейнеры, которые разработчики используют для организации файлов исходного кода и другие ресурсы, которые отображаются в **обозревателе решений**. Как правило проекты, файлы (например, CSPROJ-файл для проекта C#), которых хранятся ссылки на файлы исходного кода и ресурсы, такие как файлы точечных рисунков. Проекты позволяют организовать, построения, отладки и развертывания исходного кода, ссылки на веб-служб и баз данных и другие ресурсы. Пакеты VSPackage может расширить система проектов Visual Studio тремя разными способами: *типов проектов*, *подтипы проекта*, и *пользовательские средства*.  
  
## <a name="in-this-section"></a>Содержание  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 *Типы проектов* добавлена поддержка новых типов проектов, например языков программирования. Например каждый язык, поддерживающий Visual Studio имеет собственный тип проекта и пример интеграции IronPython включает тип проекта для языка IronPython. Необходимо создать тип проекта для языков, отличных от C# или Visual Basic для настройки как элементы построения, отладки, развертывания и отображается в **обозревателе решений**. Дополнительные сведения см. в разделе [типы проектов](../../extensibility/internals/project-types.md).  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 *Подтипы проекта* основаны на типах проектов и может использоваться, чтобы настроить способ построения, отладки и развертывания проектов. Visual Studio использует подтипы проекта с проекты для интеллектуальных устройств; они Настройка развертывания путем копирования вновь созданного программы с компьютера разработчика на целевом устройстве. C# и типы проектов Visual Basic можно использовать как основу для подтипов проекта. Типы проектов C++ невозможно. Собственные типы проектов могут также использоваться как основу для подтипы проекта. Дополнительные сведения см. в разделе [подтипы проекта](../../extensibility/internals/project-subtypes.md).  
  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Описание веб-проект, который в свою очередь создавать веб-приложения.  
  
 [Создание нового проекта: За кулисами, часть 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) и [Создание нового проекта: за кулисами, часть 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Объясняет, что фактически происходит при создании нового проекта.  
  
 [Примеры VSSDK](http://aka.ms/vs2015sdksamples)  
 Содержит образцы в VSSDK, которые имеют дело с проектами и решениями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Компоненты пакета SDK для Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Описаны различные аспекты расширяемости Visual Studio.