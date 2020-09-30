---
title: Расширения редактора и языковой службы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43048ee57e51b80becc12b282f86c971f65bef16
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584585"
---
# <a name="editor-and-language-service-extensions"></a>Расширения редактора и языковой службы
Большинство функций редактора кода Visual Studio можно расширить. Редактор основан на Windows Presentation Foundation (WPF) и написан в управляемом коде. Хотя этот проект отличается от дизайна в предыдущих версиях Visual Studio, он предоставляет большинство функций. Чтобы расширить редактор, используйте Managed Extensibility Framework (MEF).

 Пакет SDK для Visual Studio предоставляет адаптеры, называемые *оболочками совместимости* , для поддержки пакетов VSPackage, написанных для более ранних версий. Тем не менее, если у вас уже есть пакет VSPackage, рекомендуется обновить его до новой технологии, чтобы получить лучшую производительность и надежность.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Общие сведения об использовании шаблонов элементов редактора.|
|[Расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы со сведениями о проектировании и функциях базового редактора и о том, как его расширить.|
|[Устаревшие интерфейсы в редакторе](../vs-2015/extensibility/legacy-interfaces-in-the-editor.md?view=vs-2015&preserve-view=true)|Ссылки на документы, объясняющие, как получить доступ к основному редактору из существующего кода.|
|[Создание пользовательских редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, в которых объясняется, как создавать пользовательские редакторы.|
|[Расширяемость языковой службы прежних версий](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, в которых описывается интеграция языков программирования в Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Вводит Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Вводит Windows Presentation Foundation (WPF).|