---
title: Специальные возможности
description: В этой статье описаны специальные возможности в Visual Studio для Mac и способы их включения.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.topic: overview
ms.openlocfilehash: a2f151cbf593d2b8e26be7ac60eaf8ff3c687499
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938916"
---
# <a name="accessibility"></a>Специальные возможности

Кроме функций и служебных программ для macOS, Visual Studio для Mac предоставляет дополнительные возможности для людей с ограниченными возможностями:

- увеличение текста в панелях решения и редактора;
- настройка размера текста в редакторах;
- настройка цвета в редакторах;
- настройка сочетаний клавиш;
- автозавершение методов и параметров.

Дополнительные сведения о специальных возможностях для macOS см. на [веб-сайте Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Использование специальных возможностей в Visual Studio для Mac

Специальные возможности в Visual Studio для Mac отключены по умолчанию. Включить их можно так:

1. Последовательно выберите **Visual Studio > Preferences > Other > Accessibility** (Visual Studio > Параметры > Другое > Специальные возможности).

2. Установите флажок **Enable Accessibility** (Включить специальные возможности), как показано ниже:

    ![Установка флажка специальных возможностей](media/accessibility-image1.png)

3. Нажмите кнопку **Restart Visual Studio** (Перезапустить Visual Studio), чтобы изменения вступили в силу.

Также включить специальные возможности можно в командной строке. Для этого введите следующую команду в окне терминала:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Включив специальные возможности, перезапустите Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Практическое руководство. Навигация с помощью клавиатуры

Навигацию с помощью клавиатуры можно включить, выбрав **System Preferences > Keyboard > Shortcuts** (Системные настройки > Клавиатура > Ярлыки) и установив для параметра Full Keyboard Access (Полный доступ с клавиатуры) значение **All Controls** (Все элементы управления):

![Панель системных настроек в macOS](media/accessibility-image2.png)

Настройка параметра доступа с клавиатуры включает прямоугольник фокуса. Теперь элементы управления можно выбирать следующим образом:

- используя клавишу TAB для перехода по элементам управления вперед;
- используя клавиши SHIFT+TAB для перехода по элементам управления назад;
- используя клавиши со стрелками для перемещения между элементами управления в направлении стрелки.

Нажатие клавиши ПРОБЕЛ активирует элемент управления с наведенным фокусом.

## <a name="how-to-enable-and-use-voice-over"></a>Практическое руководство. Включение и использование функции VoiceOver

Чтобы включить или отключить функцию VoiceOver, нажмите клавиши **CMD+F5**.

Для навигации между командами пользовательского интерфейса VoiceOver используйте следующие команды:

- Перемещение курсора VoiceOver между элементами управления: **CTRL + ALT + клавиша со стрелкой влево / клавиша со стрелкой вправо**

   VoiceOver считывает имя элементов управления и некоторые сведения о них, а также определяет возможные действия с ними.

- Ввод групп и элементов управления (например, панели решения, панели инструментов и других панелей): **CTRL+ALT+SHIFT+СТРЕЛКА ВНИЗ**

   Перемещаться в пределах элемента управления можно с помощью клавиш **CTRL+ALT+СТРЕЛКИ**.

Общие сведения об использовании VoiceOver в macOS см. в следующих руководствах:

- [VoiceOver Getting Started Guide](https://help.apple.com/voiceover/info/guide/10.12/) (Руководство по началу работы с VoiceOver)
- [OS X VoiceOver Commands](https://lab.dotjay.com/notes/voiceover-commands/) (Команды VoiceOver в OS X)

## <a name="see-also"></a>См. также

- [Специальные возможности Visual Studio (в Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)