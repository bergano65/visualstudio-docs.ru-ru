---
title: Настройка цветовой темы и шрифтов
ms.date: 03/23/2020
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c0b7b4e439f33e4e2eed8609d7e85e098068aea
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233149"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Персонализация интегрированной среды разработки и редактора Visual Studio

В этом кратком (на 5 –10 минут) учебнике мы настроим для Visual Studio цветовую тему, выбрав темную тему. Мы также настроим цвета для двух разных типов текста в текстовом редакторе.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range=">=vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads), если еще не сделали этого.

::: moniker-end

## <a name="set-the-color-theme"></a>Настройка цветовой темы

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

## <a name="change-text-color"></a>Изменение цвета текста

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

Мы изучили только некоторые способы настраивать цвета в Visual Studio. Ознакомьтесь с другими возможностями в диалоговом окне **Параметры**, чтобы настроить Visual Studio в соответствии со своими предпочтениями.

## <a name="see-also"></a>См. также

- [Настройка редактора](../ide/how-to-change-text-case-in-the-editor.md)
- [Обзор интегрированной среды разработки Visual Studio IDE](../get-started/visual-studio-ide.md)
