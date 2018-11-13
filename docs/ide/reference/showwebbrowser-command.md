---
title: Команда ShowWebBrowser
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87536df138de092948d845cf05d20af8e63ad68a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672149"
---
# <a name="showwebbrowser-command"></a>Команда ShowWebBrowser

Предназначена для отображения URL-адреса, указанного в окне браузера внутри или вне интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Аргументы
 `URL`

 Обязательно. URL-адрес для веб-сайта.

## <a name="switches"></a>Переключатели
 /new

 Необязательный. Указывает, что страница отображается в новом экземпляре браузера.

 /ext

 Необязательный. Указывает, что страница отображается в браузере по умолчанию вне интегрированной среды разработки.

## <a name="remarks"></a>Примечания
 Псевдоним для команды **ShowWebBrowser** имеет значение **navigate** или **nav**.

## <a name="example"></a>Пример
 Следующий пример отображает домашнюю страницу сайта "Документация Майкрософт" в веб-браузере вне интегрированной среды разработки. Если экземпляр веб-браузера уже открыт, то используется он. В противном случае запускается новый экземпляр.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)