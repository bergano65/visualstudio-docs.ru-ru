---
title: Редактор и языковой службы расширения | Документы Microsoft
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
ms.openlocfilehash: d2fceb0487c23dc34d3f4f4937d7a5998340ae3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="editor-and-language-service-extensions"></a>Редактор и расширения службы языка
Можно расширить большинство возможностей в редакторе кода Visual Studio. Редактор основан на Windows Presentation Foundation (WPF) и записана в управляемом коде. Несмотря на то, что такой подход отличается от схемы, в более ранних версиях Visual Studio, он предоставляет большинство тех же функций. Чтобы расширить редактор, следует используйте Managed Extensibility Framework (MEF).  
  
 Пакет SDK для Visual Studio предоставляет адаптеров, известный как *оболочки* для поддержки пакетов VSPackage, написанные для предыдущих версий. Тем не менее при наличии существующего пакета VSPackage, рекомендуется обновить его до новой технологии, чтобы получить более высокую производительность и надежность.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Общие сведения об использовании шаблонов элементов редактора.|  
|[Расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы, разработки, а также возможности редактора основных компонентов и показано, как расширить ее.|  
|[Устаревшие интерфейсы в редакторе](../extensibility/legacy-interfaces-in-the-editor.md)|Ссылки на документы, в которых объясняется, как получить доступ к базового редактора из существующего кода.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, в которых описаны способы создания пользовательских редакторов.|  
|[Расширяемость языковой службы прежних версий](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, в которых описывается интеграция языков программирования в Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Вводит Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Вводит Windows Presentation Foundation (WPF).|