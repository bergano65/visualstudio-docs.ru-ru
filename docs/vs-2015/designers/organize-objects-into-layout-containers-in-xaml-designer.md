---
title: Упорядочивание объектов в макеты-контейнеры в конструкторе XAML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ca6fc205585d832f4dadc5f4ce4709a71c7b6fe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059205"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Упорядочивание объектов в макеты-контейнеры в конструкторе XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представьте, как бы вы хотели расположить на странице такие объекты, как изображения, кнопки и видеозаписи. Возможно, необходимо отобразить их в строку или в столбец, в одну линию по вертикали или по горизонтали или в фиксированных позициях.  
  
 После того как вы распланировали структуру страницы, выберите панель макета. Создание любой страницы начинается с одного и того же, поскольку вам необходима база, для которой будут добавляться все объекты. По умолчанию это **Сетка**, но этот параметр можно изменить.  
  
 Панели макета помогут упорядочить объекты на странице, а также предоставят дополнительные возможности. Они помогут разработать страницы с учетом различных размеров и разрешений экрана. При запуске приложения размер всех элементов на панели макета изменяется в соответствии с действительными размерами экрана данного устройства. Конечно, если вам не требуется изменения размера, то вы можете переопределить это поведение для части макета или всего макета. Для этого можно использовать свойства высоты и ширины.  
  
 Эта страница содержит описание панелей макета и элементов управления и ссылки на видеоролики, которые помогут вам приступить к работе с данными элементами.  
  
> [!NOTE]
>  Некоторые из видео могут ссылаться на Blend или Expression Blend, которые используют тот же конструктор XAML, что и Visual Studio и Blend для Visual Studio.  
  
## <a name="layout-panels"></a>Панели макета  
 Запустите страницу, выбрав одну из таких панелей макета. Ваша страница может иметь несколько панелей макета. Например, вы можете начать работу с панели макета **Сетка**, а затем добавить в определенную область **Сетки** элемент **StackPanel**, чтобы можно было расположить элементы управления по вертикали в этой области.  
  
 Следующие панели макета используются наиболее часто, но существуют и другие. Их можно найти на панели **Ресурсы**.  
  
- [Сетка](#Grid)  
  
- [UniformGrid](#Uniform)  
  
- [Canvas](#Canvas)  
  
- [StackPanel](#Stack)  
  
- [WrapPanel](#Wrap)  
  
- [DockPanel](#Dock)  
  
### <a name="Grid"></a> Сетка  
 Упорядочивание объектов по строкам и столбцам.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [с помощью сетки](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
### <a name="Uniform"></a> UniformGrid  
 Равномерное или однородное упорядочивание объектов в областях сетки. Эта панель отлично подходит для упорядочивания списка изображений.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Доступно только для проектов WPF)  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [работа с UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
### <a name="Canvas"></a> Canvas  
 Упорядочивание объектов любым образом При запуске приложения пользователями эти элементы будут иметь фиксированные позиции на экране.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [работа с холстом](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
### <a name="Stack"></a> StackPanel  
 Расположение объектов в одну линию по вертикали или по горизонтали.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [работа с элементами StackPanel и WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Wrap"></a> WrapPanel  
 Упорядочивание объектов последовательно в направлении слева направо. Когда место закончится и строка достигнет края справа, то панель *перенесет* содержимое на следующую строку, и так будет повторяться раз за разом слева направо и сверху вниз. Вы также можете задать вертикальную ориентацию панели с переносом, чтобы объекты переносились в другой очередности: сверху вниз и слева направо.  
  
 (Доступно только для проектов WPF)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [работа с элементами StackPanel и WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Dock"></a> DockPanel  
 Размещение элементов происходит таким образом, чтобы они оставались или были *закрепленными* у одного края панели.  
  
 (Доступно только для проектов WPF)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF — DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Элементы управления макета  
 Вы также можете добавить объекты к элементам управления. Они не так многофункциональны, как панель макета, но также могут оказаться полезными в определенных случаях.  
  
 Следующие элементы управления макета используются наиболее часто, но существуют и другие. Их можно найти на панели **Ресурсы**.  
  
- [Border](#Border)  
  
- [Контекстное меню](#Popup)  
  
- [ScrollViewer](#Scroll)  
  
- [UniformGrid](#Uniform)  
  
- [Viewbox](#View)  
  
### <a name="Border"></a> Граница  
 Создайте границу, фон или одновременно границу и фон вокруг объекта. Для **границы** можно добавить только один объект. Если вы хотите применить границу или фон для нескольких объектов, добавьте панель макета для **границы**. Затем добавьте объекты для панели или элемента управления.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [работа с границами](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
### <a name="Popup"></a> Всплывающее окно  
 Отображение информации или параметров для пользователей в окне. Для элемента **Всплывающее окно** можно добавить только один объект. По умолчанию **Всплывающее окно** содержит **Сетку**, но этот параметр можно изменить.  
  
### <a name="Scroll"></a> ScrollViewer  
 Позволяет пользователям прокручивать вниз страницу или часть страницы. Для элемента **ScrollViewer** можно добавить только один объект, поэтому очень важно добавить панель макета, например **сетку** или **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
### <a name="View"></a> Viewbox  
 Масштабирование объектов способом, аналогичным масштабированию с помощью элемента управления масштабом. Для панели **Viewbox** можно добавить только один объект. Чтобы применить этот эффект к нескольким объектам, добавьте панель макета для **ViewBox**, а затем добавьте элементы управления для этой панели макета.  
  
 (Доступно только для проектов WPF)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>См. также  
 [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [Создание пользовательского интерфейса с помощью конструктора XAML в Visual Studio](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
