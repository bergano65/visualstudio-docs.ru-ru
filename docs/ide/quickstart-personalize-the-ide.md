---
title: "Настройка шрифтов и цветовых тем в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e5195693a4ef2ba3aeec1f2d5751e56b70f19e57
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Краткое руководство. Персонализация интегрированной среды разработки и редактора Visual Studio

В этом кратком (на 5–10 минут) руководстве мы настроим для Visual Studio цветовую тему и два цвета текста в текстовом редакторе.

## <a name="set-the-color-theme"></a>Настройка цветовой темы

По умолчанию в Visual Studio 2017 установлена тема **Синяя**. Давайте изменим ее на тему **Темная**.

1. В строке меню выберите **Сервис**, **Параметры**.

1. В разделе **Среда** откройте страницу **Общие**, измените значение параметра **Цветовая тема** на **Темная** и нажмите кнопку **ОК**.

   Цветовая тема для всей интегрированной среды разработки изменится на тему **Темная**.

   ![VS с темой "Темная"](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Вы можете выбрать дополнительные предопределенные темы, установив **редактор цветовых тем Visual Studio** из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2017ColorThemeEditor). Когда вы установите это средство, в раскрывающемся списке с цветовыми темами появятся дополнительные темы.

## <a name="change-text-color"></a>Изменение цвета текста

Теперь настроим несколько цветов текста для редактора. Сначала откроем XML-файл, чтобы просмотреть цвета по умолчанию.

1. В строке меню выберите **Файл**, **Создать**, **Файл...**

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

   Обратите внимание, что цвет номеров строк бирюзовый, а атрибутов XML — голубой. Давайте изменим цвет этих элементов.

   ![Цвета шрифта в файле XML](media/quickstart-personalize-xml-file.png)

1. Чтобы открыть диалоговое окно **Параметры**, в строке меню выберите **Инструменты**, **Параметры**.

1. В разделе **Среда** выберите категорию **Шрифты и цвета**.

   Обратите внимание, что в поле **Показать параметры для** указано значение **Текстовый редактор**,&mdash;именно это нам и нужно. Вы можете раскрыть список, чтобы узнать, для каких еще элементов можно настроить шрифты и цвет текста.

1. Чтобы изменить цвет номера строки, в списке **Отображение элементов** выберите **Номер строки**. В поле **Основной цвет элемента** выберите **Оливковый**.

   ![Диалоговое окно "Параметры", раздел "Шрифты и цвета"](media/quickstart-personalize-line-number-color.png)

   Некоторые языки имеют собственные параметры шрифтов и цветов. Если вы являетесь разработчиком на C++ и хотите изменить цвет, используемый для выделения функций, найдите элемент **Функции C++** в списке **Отображение элементов**.

1. Прежде чем закрыть диалоговое окно, давайте также изменим цвет атрибутов XML. В списке **Отображение элементов** прокрутите вниз до элемента **Атрибут XML** и выберите его. В поле **Основной цвет элемента** выберите **Травяной**. Нажмите **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.

   Теперь цвет номеров строк станет оливковым, а цвет XML-атрибутов — ярко-травяным. Если открыть файл другого типа, например файл с кодом C++ и C#, цвет номеров строк также станет оливковым.

   ![XML-файл с новыми цветами шрифта](media/quickstart-personalize-xml-file-new-colors.png)

Мы изучили только некоторые способы настраивать цвета в Visual Studio. Ознакомьтесь с другими возможностями в диалоговом окне **Параметры**, чтобы настроить Visual Studio в соответствии со своими предпочтениями.

## <a name="see-also"></a>См. также

[Краткое руководство. Знакомство с интегрированной средой разработки Visual Studio](../ide/quickstart-ide-orientation.md)  
[Краткое руководство. Написание кода в редакторе](../ide/quickstart-editor.md)  
[Краткое руководство. Проекты и решения](../ide/quickstart-projects-solutions.md)  
[Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md)  
[Настройка редактора](../ide/customizing-the-editor.md)  
[Обзор интегрированной среды разработки Visual Studio IDE](../ide/visual-studio-ide.md)