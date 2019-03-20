---
title: Настройка цветовой темы и шрифтов
ms.date: 11/20/2017
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 504b33ee897ac59b7fe55625a67a01b8dca8ff32
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "57869335"
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Краткое руководство. Персонализация интегрированной среды разработки и редактора Visual Studio

В этом кратком (на 5–10 минут) руководстве мы настроим для Visual Studio цветовую тему, выбрав темную тему. Мы также настроим цвета для двух разных типов текста в текстовом редакторе.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), если еще не сделали этого.

## <a name="set-the-color-theme"></a>Настройка цветовой темы

По умолчанию в пользовательском интерфейсе Visual Studio установлена тема **Синяя**. Давайте изменим ее на тему **Темная**.

1. В строке меню, где расположены разделы **Файл** и **Изменить**, выберите **Средства** > **Параметры**.

1. На странице параметров **Среда** > **Общие** измените значение параметра **Цветовая тема** на **Темная** и нажмите кнопку **ОК**.

   Цветовая тема для всей среды разработки (IDE) Visual Studio изменяется на **Темная**.

   ![VS с темной темой](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Вы можете выбрать дополнительные предопределенные темы, установив **редактор цветовых тем Visual Studio** из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Когда вы установите это средство, в раскрывающемся списке **Цветовая тема** появятся дополнительные темы.

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

- [Настройка редактора](../ide/customizing-the-editor.md)
- [Обзор интегрированной среды разработки Visual Studio IDE](../get-started/visual-studio-ide.md)