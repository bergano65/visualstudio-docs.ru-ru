---
title: JavaScript и TypeScript
description: Сведения о поддержке JavaScript в Visual Studio для Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 7839b3ed777de134bea835c94c428166ea4430f4
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107854"
---
# <a name="javascript-and-typescript-support"></a>Поддержка JavaScript и TypeScript

Visual Studio для Mac обеспечивает поддержку JavaScript и TypeScript посредством подсветки синтаксиса, форматирования кода и технологии IntelliSense.

![поддержка typescript в редакторе](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Дополнительные сведения о программировании на JavaScript см. в руководстве [Написание кода JavaScript](/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Добавление файла JavaScript

Наиболее часто файлы JavaScript добавляются в проекты ASP.NET Core через диалоговое окно **Новый файл**. Чтобы добавить файл javascript, щелкните правой кнопкой мыши на проекте и выберите **Добавить > Новый файл**:

![добавление новых файлов в проект](media/javascript-image1.png)

В диалоговом окне **создания файла** выберите **Интернет > Пустой JS-файл** или **Интернет > Файл TypeScript**. Введите имя файла и нажмите кнопку **Создать**:

![создание нового файла typescript из шаблона](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio для Mac использует [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) для предоставления возможностей IntelliSense при написании кода, а именно: интеллектуальное завершение кода, сведения о параметрах и списки членов.

IntelliSense для JavaScript в Visual Studio для Mac может опираться на определение типов, JSDoc или объявлений TypeScript.

- **Определение типа** — тип объекта определяется окружающему контексту кода. Дополнительные сведения см. в разделе [IntelliSense на основе определения типа](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference) документации по Visual Studio.
- **JSDoc** — бывают случаи, когда определение типа не предоставляет правильные сведения о типе. В этих случаях сведения о типе предоставляются явно с помощью заметок [JSDoc](https://jsdoc.app/about-getting-started.html). Дополнительные сведения см. в разделе [IntelliSense на основе JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) документации по Visual Studio
- **Файл объявлений TypeScript** — файлы `.d.ts`, используемые для предоставления значений для IntelliSense для JavaScript. Типы, объявленные в этом файле, могут использоваться как типы в комментариях JSDoc. Дополнительные сведения см. в разделе [IntelliSense на основе файлов объявления TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) документации по Visual Studio.

    ![Добавление файла определения TypeScript](media/javascript-image3.png)

## <a name="see-also"></a>См. также

- [JavaScript IntelliSense (Visual Studio в Windows)](/visualstudio/ide/javascript-intellisense)
