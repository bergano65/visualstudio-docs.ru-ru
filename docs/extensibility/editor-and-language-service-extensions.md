---
title: Расширения службы редактора и языка (ru) Документы Майкрософт
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
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712024"
---
# <a name="editor-and-language-service-extensions"></a>Расширение службы редактора и языка
Вы можете расширить большинство функций редактора кода Visual Studio. Редактор основан на Windows Presentation Foundation (WPF) и написан в управляемом коде. Хотя этот дизайн отличается от конструкций в более ранних версиях Visual Studio, он предоставляет большинство из тех же функций. Для расширения редактора используйте Рамочную рамку управляемого расширения (MEF).

 Visual Studio SDK предоставляет адаптеры, известные как *очерки* для поддержки VSPackages, которые были написаны для более ранних версий. Тем не менее, если у вас есть существующий VSPackage, мы рекомендуем вам обновить его до новой технологии, чтобы получить лучшую производительность и надежность.

## <a name="related-topics"></a>Связанные разделы

|Заголовок|Описание|
|-----------|-----------------|
|[Создание расширения с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Введение в использование шаблонов элементов редактора.|
|[Расширить службы редактора и языка](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы, которые вводят дизайн и особенности основного редактора и показывают, как его расширить.|
|[Устаревшие интерфейсы в редакторе](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Ссылки на документы, объясняющие доступ к основному редактору из существующего кода.|
|[Создание пользовательских редакторов и дизайнеров](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, объясняющие, как создавать пользовательские редакторы.|
|[Расширяемость устаревшей языковой службы](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, описывающие интеграцию языков программирования в Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Вводит Рамочную программу управляемого расширяемости (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Представляет Фонд презентаций Windows (WPF).|
