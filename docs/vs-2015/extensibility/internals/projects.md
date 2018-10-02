---
title: Проекты | Документация Майкрософт
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
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ade0234423c907c675bc1dd53e3436dfa38ca26e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558827"
---
# <a name="projects"></a>Проекты
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [проекты](https://docs.microsoft.com/visualstudio/extensibility/internals/projects).  
  
В Visual Studio проекты — это контейнеры, используемые разработчиками для организации файлов исходного кода и другие ресурсы, которые отображаются в **обозревателе решений**. Обычно проекты, файлы (например, CSPROJ-файл для проекта C#), в которых хранятся ссылки на файлы исходного кода и ресурсов, таких как файлы растровых изображений. Проекты позволяют организовать, построения, отладки и развертывания исходного кода, ссылки на веб-служб и баз данных и другие ресурсы. Пакеты VSPackage может расширить систему проекта Visual Studio тремя основными способами: *типы проектов*, *подтипы проекта*, и *пользовательские инструменты*.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 *Типы проектов* добавлена поддержка новых типов проектов, например языков программирования. Например каждый язык, поддерживающий Visual Studio имеет свой собственный тип проекта и пример интеграции IronPython включает тип проекта для языка IronPython. Необходимо создать тип проекта языки, отличные от C# или Visual Basic для настройки как элементов построения, отладки, развертывания и отображаются в **обозревателе решений**. Дополнительные сведения см. в разделе [типы проектов](../../extensibility/internals/project-types.md).  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 *Подтипы проекта* основаны на типах проектов и может использоваться для настройки способа построение, отладка и развертывание проектов. Visual Studio использует подтипов проекта проектов смарт-устройств; они настройки развертывания путем копирования только что созданных с помощью программы с компьютера разработчика на целевом устройстве. C# и типы проектов Visual Basic можно использовать как основу для подтипов проекта; Типы проектов C++ невозможно. Собственные типы проектов могут также использоваться как основу для подтипов проекта. Дополнительные сведения см. в разделе [подтипов проекта](../../extensibility/internals/project-subtypes.md).  
  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Описание веб-проект, который в свою очередь создают веб-приложений.  
  
 [Создание нового проекта: Взгляд изнутри, часть первая](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) и [Создание нового проекта: взгляд изнутри, часть 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Объясняет, что фактически происходит при создании нового проекта.  
  
 [Примеры VSSDK](../../misc/vssdk-samples.md)  
 Описание образцов, в VSSDK, которые имеют дело с проектами и решениями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Компоненты пакета SDK для Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Объясните различные аспекты расширяемости Visual Studio.

