---
title: Команда ShowWebBrowser
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747714"
---
# <a name="showwebbrowser-command"></a>Команда ShowWebBrowser

Предназначена для отображения URL-адреса, указанного в окне браузера внутри или вне интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Аргументы
`URL`

Обязательный элемент. URL-адрес для веб-сайта.

## <a name="switches"></a>Коммутаторы
/new

Необязательный параметр. Указывает, что страница отображается в новом экземпляре браузера.

/ext

Необязательный параметр. Указывает, что страница отображается в браузере по умолчанию вне интегрированной среды разработки.

## <a name="remarks"></a>Remarks
Псевдоним для команды **ShowWebBrowser** имеет значение **navigate** или **nav**.

## <a name="example"></a>Пример
Следующий пример отображает домашнюю страницу сайта "Документация Майкрософт" в веб-браузере вне интегрированной среды разработки. Если экземпляр веб-браузера уже открыт, то используется он. В противном случае запускается новый экземпляр.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)