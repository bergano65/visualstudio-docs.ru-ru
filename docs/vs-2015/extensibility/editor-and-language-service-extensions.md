---
title: Редактор и языковой службы расширения | Документация Майкрософт
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
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e464b46185339bd1a22b433e4784154dbdb818c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572414"
---
# <a name="editor-and-language-service-extensions"></a>Расширения редактора и языковой службы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [редактора и языковой службы расширения](https://docs.microsoft.com/visualstudio/extensibility/editor-and-language-service-extensions).  
  
Вы можете расширить большинство функций уровней в редакторе кода Visual Studio. Редактор основан на Windows Presentation Foundation (WPF) и записывается в управляемом коде. Несмотря на то, что такая схема отличается от схемы в более ранних версиях Visual Studio, он предоставляет большую часть тех же функций. Чтобы расширить редактор, используйте Managed Extensibility Framework (MEF).  
  
 Пакет SDK для Visual Studio содержит адаптеры, известный как *оболочек* для поддержки пакетов VSPackage, разработанные для более ранних версий. Тем не менее при наличии существующего пакета VSPackage, мы рекомендуем обновить его до новой технологии, чтобы получить более высокую производительность и надежность.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Общие сведения об использовании шаблонов элементов редактора.|  
|[Расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы, описывающие разработки и функций редактора core показано, как расширить его.|  
|[Интерфейсы прежних версий в редакторе](../extensibility/legacy-interfaces-in-the-editor.md)|Ссылки на документы, в которых объясняется, как получить доступ к базовым редактором из существующего кода.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, в которых описаны способы создания пользовательских редакторов.|  
|[Расширяемость языковой службы прежних версий](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, описывающие, как интегрировать языков программирования в Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Представляет Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Введение в Windows Presentation Foundation (WPF).|

