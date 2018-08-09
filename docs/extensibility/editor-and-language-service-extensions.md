---
title: Редактор и языковой службы расширения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc695e9340155572ba04753301a62f238f91242
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636470"
---
# <a name="editor-and-language-service-extensions"></a>Редактор и языковой службы расширения
Вы можете расширить большинство функций уровней в редакторе кода Visual Studio. Редактор основан на Windows Presentation Foundation (WPF) и записывается в управляемом коде. Несмотря на то, что такая схема отличается от схемы в более ранних версиях Visual Studio, он предоставляет большую часть тех же функций. Чтобы расширить редактор, используйте Managed Extensibility Framework (MEF).  
  
 Пакет SDK для Visual Studio содержит адаптеры, известный как *оболочек* для поддержки пакетов VSPackage, разработанные для более ранних версий. Тем не менее при наличии существующего пакета VSPackage, мы рекомендуем обновить его до новой технологии, чтобы получить более высокую производительность и надежность.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Общие сведения об использовании шаблонов элементов редактора.|  
|[Расширение редактора и языковой службы](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы, описывающие разработки и функций редактора core показано, как расширить его.|  
|[Устаревшие интерфейсы в редакторе](../extensibility/legacy-interfaces-in-the-editor.md)|Ссылки на документы, в которых объясняется, как получить доступ к базовым редактором из существующего кода.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, в которых описаны способы создания пользовательских редакторов.|  
|[Расширяемость устаревший языковой службы](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, описывающие, как интегрировать языков программирования в Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Представляет Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Введение в Windows Presentation Foundation (WPF).|