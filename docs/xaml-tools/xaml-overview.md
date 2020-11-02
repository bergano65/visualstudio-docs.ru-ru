---
title: Общие сведения об XAML
description: Ознакомьтесь с основными сведениями о XAML, о редакторе кода XAML и об инструментах Конструктора XAML в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 997a35414f38af16d028770044c28652e13149be
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049199"
---
# <a name="overview-of-xaml"></a>Обзор XAML

Язык XAML — это декларативный язык, основанный на XML. XAML широко используется для создания пользовательских интерфейсов в приложениях следующих типов:

- [приложения Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf);
- [приложения универсальной платформы Windows (UWP)](/windows/uwp/xaml-platform/xaml-overview);
- [приложения Xamarin.Forms](/xamarin/xamarin-forms/xaml/).

В следующем коде XAML определяется простой элемент управления "Кнопка".

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML также используется для определения рабочих процессов в [приложениях Windows WorkFlow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-code-editor"></a>Редактор кода XAML

[Редактор кода XAML](xaml-code-editor.md) в интегрированной среде разработки Visual Studio содержит все инструменты, необходимые для создания приложений WPF и UWP для платформы Windows, а также для Xamarin.Forms. Интегрированная среда разработки (IDE) в Visual Studio имеет множество функций, которые можно использовать для разработки приложений под другие платформы, у нее есть и функции, уникальные для XAML.

## <a name="xaml-designer"></a>Конструктор XAML

Visual Studio и Blend для Visual Studio предоставляют [Конструктор XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md), который помогает создавать пользовательские интерфейсы для приложений WPF, UWP и Xamarin.Forms. Вы можете перетаскивать элементы управления из панели инструментов или окна "Ресурсы" и задавать свойства в окне свойств. При выполнении этих действий Visual Studio и Blend для Visual Studio создают соответствующий код XAML. Если вы предпочитаете редактировать код XAML напрямую, это также можно сделать.

## <a name="whats-new"></a>Новые возможности

Актуальную информацию см. в следующих материалах:

- Запись блога **[Усовершенствования в инструментах XAML в Visual Studio 2019 версии 16.7, предварительная версия 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- Запись блога **[О новых возможностях средств разработчика XAML в Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- Видео на YouTube **[Новые функции XAML в Visual Studio](https://youtu.be/yI9OyA4ZM2E)**

## <a name="see-also"></a>См. также раздел

- [XAML в приложениях WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML в приложениях UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML в приложениях Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
