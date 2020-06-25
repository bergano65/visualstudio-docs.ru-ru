---
title: Общие сведения об XAML
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331952"
---
# <a name="overview-of-xaml"></a>Обзор XAML

Язык XAML — это декларативный язык, основанный на XML. XAML широко используется для создания пользовательских интерфейсов в приложениях следующих типов:

- [Приложения Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Приложения универсальная платформа Windows (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [приложения Xamarin.Forms](/xamarin/xamarin-forms/xaml/).

В следующем коде XAML определяется простой элемент управления "Кнопка".

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML также используется для определения рабочих процессов в [приложениях Windows WorkFlow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-code-editor"></a>Редактор кода XAML

[Редактор кода XAML](xaml-code-editor.md) в интегрированной среде разработки Visual Studio включает все средства, необходимые для создания приложений WPF и UWP для платформы Windows и для Xamarin. Forms. Хотя интегрированная среда разработки (IDE) в Visual Studio имеет множество функций, которые можно использовать для разработки приложений для других платформ, у нее также есть некоторые функции, которые являются уникальными для XAML.

## <a name="xaml-designer"></a>Конструктор XAML

Visual Studio и Blend для Visual Studio предоставляют [конструктор XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) , который помогает создавать пользовательские интерфейсы для приложений WPF, UWP и Xamarin. Forms. Вы можете перетаскивать элементы управления из панели инструментов или окна "Ресурсы" и задавать свойства в окне свойств. При этом Visual Studio и Blend для Visual Studio создают соответствующий код XAML. Если вы предпочитаете редактировать код XAML напрямую, это также можно сделать.

## <a name="whats-new"></a>Новые возможности

Последние сведения см. в следующих ресурсах:

- **[Улучшения в средствах XAML в записи блога по Visual Studio 2019 версии 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- **[Новые возможности средств РАЗРАБОТЧИКА XAML в записи блога Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- **[Новые возможности XAML в видео Visual Studio](https://youtu.be/yI9OyA4ZM2E)** на YouTube

## <a name="see-also"></a>См. также

- [XAML в приложениях WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML в приложениях UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML в приложениях Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
