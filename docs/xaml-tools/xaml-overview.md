---
title: Общие сведения об XAML
ms.date: 01/10/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2556387f523769bba93708a9c00d1f7c62429c0f
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "82921229"
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

## <a name="xaml-designer"></a>Конструктор XAML

Visual Studio и Blend для Visual Studio предоставляют Конструктор XAML, который помогает создавать пользовательские интерфейсы для приложений WPF, UWP и Xamarin.Forms. Вы можете перетаскивать элементы управления из панели инструментов или окна "Ресурсы" и задавать свойства в окне свойств. При этом Visual Studio и Blend для Visual Studio создают соответствующий код XAML. Если вы предпочитаете редактировать код XAML напрямую, это также можно сделать.

В статьях этого набора документации рассматривается Конструктор XAML в Visual Studio и Blend для Visual Studio.

## <a name="whats-new"></a>Новые возможности

Последние сведения см. в статье [что нового в средствах РАЗРАБОТЧИКА XAML статьи в блоге Visual studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) и [новых функциях XAML в видео Visual Studio](https://youtu.be/yI9OyA4ZM2E) на YouTube.

## <a name="see-also"></a>См. также раздел

- [XAML в приложениях WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML в приложениях UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML в приложениях Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
