---
title: Задание темной темы и изменение цвета текста в Visual Studio
description: Сведения о том, как изменить цветовую тему Visual Studio по умолчанию на темный режим, а также как изменить цвета шрифтов в редакторе кода.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb7c9bf04e5f38e5138eae6cf6254bb77bbd6230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916065"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Практическое руководство. Персонализация интегрированной среды разработки и редактора Visual Studio

Из этой статьи вы узнаете, как переключить цветовую тему Visual Studio по умолчанию на темный режим. Мы также настроим цвета для двух различных типов текста в редакторе кода.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range=">=vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Настройка цветовой темы для интегрированной среды разработки

По умолчанию в пользовательском интерфейсе Visual Studio установлена тема **Синяя**. Давайте изменим ее на тему **Темная**.

1. В строке меню, где расположены разделы **Файл** и **Изменить**, выберите **Средства** > **Параметры**.

1. Откройте страницу параметров **Окружение**  > **Общие**, измените значение **Цветовая тема** на **Темная** и щелкните **ОК**.

   Цветовая тема для всей среды разработки (IDE) Visual Studio изменяется на **Темная**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 в темной теме](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 в темной теме](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Вы можете выбрать дополнительные предопределенные темы, установив **редактор цветовых тем Visual Studio** из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Когда вы установите это средство, в раскрывающемся списке **Цветовая тема** появятся дополнительные темы.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Вы можете создать собственные темы, установив **конструктор цветовых тем Visual Studio** из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Изменение цветов текста в редакторе

Теперь настроим несколько цветов текста для редактора. Сначала создадим XML-файл, чтобы просмотреть цвета по умолчанию.

1. В строке меню выберите **Файл** > **Создать** > **Файл**.

1. В диалоговом окне **Новый файл** в разделе **Общие** выберите **XML-файл** и нажмите кнопку **Открыть**.

1. Вставьте приведенный ниже XML-код под строкой с `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Обратите внимание, что цвет номеров строк бирюзовый, а атрибутов XML (например `id="bk101"`) — голубой. Давайте изменим цвет этих элементов.

   ![Цвета шрифта в файле XML](media/quickstart-personalize-xml-file.png)

1. Чтобы открыть диалоговое окно **Параметры**, в строке меню выберите **Сервис** > **Параметры**.

1. В разделе **Среда** выберите категорию **Шрифты и цвета**.

   Обратите внимание, что в поле **Показать параметры для** указано значение **Текстовый редактор**,&mdash;именно это нам и нужно. Раскройте список, чтобы узнать, для каких еще элементов можно настроить шрифты и цвет текста.

1. Чтобы изменить цвет номера строки, в списке **Отображение элементов** выберите **Номер строки**. В поле **Основной цвет элемента** выберите **Оливковый**.

   ![Диалоговое окно "Параметры", раздел "Шрифты и цвета"](media/quickstart-personalize-line-number-color.png)

   Некоторые языки имеют собственные параметры шрифтов и цветов. Если вы являетесь разработчиком на C++ и хотите изменить цвет, используемый для выделения функций, найдите элемент **Функции C++** в списке **Отображение элементов**.

1. Прежде чем закрыть диалоговое окно, давайте также изменим цвет атрибутов XML. В списке **Отображение элементов** прокрутите вниз до элемента **Атрибут XML** и выберите его. В поле **Основной цвет элемента** выберите **Травяной**. Нажмите **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.

   Теперь цвет номеров строк станет оливковым, а цвет XML-атрибутов — ярко-травяным. Если открыть файл другого типа, например файл с кодом C++ и C#, цвет номеров строк также станет оливковым.

   ![XML-файл с новыми цветами шрифта](media/quickstart-personalize-xml-file-new-colors.png)

Мы изучили только некоторые способы настраивать цвета в Visual Studio. Ознакомьтесь с другими возможностями в диалоговом окне [**Параметры**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), чтобы настроить Visual Studio в соответствии со своими предпочтениями.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Изменение шрифтов, цветов и тем в Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Практическое руководство. Изменение регистра текста в редакторе](../ide/how-to-change-text-case-in-the-editor.md)
- [Обзор интегрированной среды разработки Visual Studio](../get-started/visual-studio-ide.md)
