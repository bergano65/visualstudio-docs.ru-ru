---
title: Нет доступных источников | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f08ed499e61e54ffbc6508bc8353ea955d9a20c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730862"
---
# <a name="no-source-available"></a>Исходный код недоступен
Проект не содержит исходного кода для кода, который вы пытаетесь просмотреть. Обычно это происходит, когда в окне **Стек вызовов** или **Потоки** производится двойной щелчок по модулю, который не имеет исходного кода. Можно продолжить отладку, но невозможно использовать окно с исходным кодом для установки точек останова и выполнения других действий в этом месте. Если необходимо установить точку останова, следует использовать **окно дизассемблирования**.

 На страницах свойств решения можно поменять каталоги, в которых отладчик ищет исходные файлы, и указать отладчику пропускать выбранные исходные файлы. См. раздел [исходные файлы отладки, общие свойства, диалоговое окно страницы свойств решения](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Обзор для поиска исходного кода** Щелкните эту ссылку, чтобы открыть диалоговое окно, в котором можно перейти к поиску исходного кода.

 **Показывать дизассемблированный код** Запускает **окно дизассемблирования**.

 **Всегда показывать Дизассемблированный код для отсутствующих исходных файлов** Выберите этот параметр, чтобы **окно дизассемблирования** автоматически отображалось, если источник недоступен. Этот параметр также можно изменить в диалоговом окне **Параметры** (категория **Отладка**, страница **Общие**), установив или сняв флажок **Показывать дизассемблированный код, если исходный код недоступен**.

## <a name="see-also"></a>См. также
- [Страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно "Страницы свойств решения"](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (расширение отладки SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)