---
title: Практическое руководство. Обновление настраиваемой начальной страницы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: abe1013d37db43114f3970f12b1a0d1f08b07a4e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446460"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Практическое руководство. Обновление настраиваемой начальной страницы Visual Studio
Вы можете обновить настраиваемую начальную страницу Visual Studio 2010 или Visual Studio 2012 до версии Visual Studio 2015, выполнив описанные ниже действия.

> [!WARNING]
> В этой процедуре обновляется настраиваемая начальная страница, созданная с помощью шаблона [Настраиваемая начальная страница](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) из коллекции Visual Studio. Начальная страница может иметь и другие компоненты, требующие обновления.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Обновление настраиваемой начальной страницы до версии Visual Studio 2015

1. Убедитесь в том, что установлены среда Visual Studio 2015 и пакет SDK для Visual Studio 2015. Пакет SDK для Visual Studio можно скачать на странице [Пакет SDK для Microsoft Visual Studio 2013](https://my.visualstudio.com/Downloads?pid=1436).

2. Откройте проект настраиваемого шаблона. Вы увидите сообщение с уведомлением о том, что проект необходимо обновить. Нажмите кнопку **ОК** и дождитесь завершения обновления.

3. В свойствах проекта начальной страницы и проекта элемента управления убедитесь в том, что целевой платформой является по крайней мере .NET Framework 4.5.

4. В категории "Отладка" свойств проекта начальной страницы задайте путь к версии Visual Studio 2015 программы devenv.exe.

5. В ссылках для обоих проектов удалите ссылки на Microsoft.VisualStudio.Shell.11.0 и добавьте ссылки на Microsoft.VisualStudio.Shell.14.0.

6. Откройте файл StartPage.xaml в редакторе XML и внесите указанные ниже изменения.

    1. Обновите пространства имен. Измените следующие строки:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         на следующие:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Откройте файл MyControl.xaml и измените ссылку на пространство имен `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` на `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .