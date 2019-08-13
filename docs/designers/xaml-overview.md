---
title: Общие сведения об XAML
ms.date: 07/31/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9b04012e2f0b046b3fd31058c9838740e833281
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68823920"
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

## <a name="xaml-designer"></a>Конструктор XAML

Visual Studio и Blend для Visual Studio предоставляют Конструктор XAML, который помогает создавать пользовательские интерфейсы для приложений WPF, UWP и Xamarin.Forms. Вы можете перетаскивать элементы управления из панели инструментов или окна "Ресурсы" и задавать свойства в окне свойств. При выполнении этих действий Visual Studio и Blend для Visual Studio создают соответствующий код XAML. Если вы предпочитаете редактировать код XAML напрямую, это также можно сделать.

В статьях этого набора документации рассматривается Конструктор XAML в Visual Studio и Blend для Visual Studio.

## <a name="see-also"></a>См. также

- [XAML в приложениях WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML в приложениях UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML в приложениях Xamarin.Forms](/xamarin/xamarin-forms/xaml/)