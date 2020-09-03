---
title: Команда ShowWebBrowser | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663521"
---
# <a name="showwebbrowser-command"></a>Команда ShowWebBrowser
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает URL-адрес, указанный в окне браузера внутри или вне интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Аргументы
 `URL` Обязательный. URL-адрес для веб-сайта.

## <a name="switches"></a>Коммутаторы
 /New необязательный. Указывает, что страница отображается в новом экземпляре браузера.

 /ext (необязательно). Указывает, что страница отображается в браузере по умолчанию вне интегрированной среды разработки.

## <a name="remarks"></a>Remarks
 Псевдоним для команды **ShowWebBrowser** имеет значение **navigate** или **nav**.

## <a name="example"></a>Пример
 Следующий пример отображает домашнюю страницу сайта MSDN в веб-браузере вне интегрированной среды разработки. Если экземпляр веб-браузера уже открыт, то используется он, в противном случае запускается новый экземпляр.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>См. также:
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
