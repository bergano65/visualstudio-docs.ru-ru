---
title: Редактор и языковой службы расширения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1df6f65db70425650fc2860bf5ddf6e2d2e203c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353383"
---
# <a name="editor-and-language-service-extensions"></a>Редактор и языковой службы расширения
Вы можете расширить большинство функций уровней в редакторе кода Visual Studio. Редактор основан на Windows Presentation Foundation (WPF) и записывается в управляемом коде. Несмотря на то, что такая схема отличается от схемы в более ранних версиях Visual Studio, он предоставляет большую часть тех же функций. Чтобы расширить редактор, используйте Managed Extensibility Framework (MEF).

 Пакет SDK для Visual Studio содержит адаптеры, известный как *оболочек* для поддержки пакетов VSPackage, разработанные для более ранних версий. Тем не менее при наличии существующего пакета VSPackage, мы рекомендуем обновить его до новой технологии, чтобы получить более высокую производительность и надежность.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Общие сведения об использовании шаблонов элементов редактора.|
|[Расширение редактора и языковой службы](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы, описывающие разработки и функций редактора core показано, как расширить его.|
|[Устаревшие интерфейсы в редакторе](../extensibility/legacy-interfaces-in-the-editor.md)|Ссылки на документы, в которых объясняется, как получить доступ к базовым редактором из существующего кода.|
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, в которых описаны способы создания пользовательских редакторов.|
|[Расширяемость устаревший языковой службы](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, описывающие, как интегрировать языков программирования в Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Представляет Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Введение в Windows Presentation Foundation (WPF).|