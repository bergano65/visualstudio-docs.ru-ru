---
title: Страница "Исходные файлы отладки", диалоговое окно страниц свойств решения
description: Перейдите на страницу свойств "Исходные файлы отладки" в Visual Studio, щелкнув правой кнопкой мыши решение в окне "Обозреватель решений" и выбрав элементы "Свойства" > "Общие свойства".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10818f473dec392364832cdc2f5215197ef4627f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873175"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно "Страницы свойств решения"
Эта страница свойств задает место, где отладчик будет осуществлять поиск исходных файлов при отладке решения.

 Чтобы зайти на страницу свойств **Исходные файлы отладки**, щелкните правой кнопкой мыши решение в окне **Обозреватель решений**, а затем выберите пункт **Свойства** в меню быстрого вызова. Разверните папку **Общие свойства** и выберите страницу **Исходные файлы отладки**.

 **Каталоги, содержащие исходный код**. Список каталогов, в которых отладчик ищет исходные файлы при отладке решения. Поиск также производится внутри подкаталогов заданных каталогов.

 **Не выполнять поиск следующих исходных файлов**. Введите имена файлов, которые отладчик не должен считывать. Если отладчик найдет один из этих файлов в одном из указанных каталогов, отладчик пропустит этот файл. Если во время отладки появится диалоговое окно **Поиск исходного текста** и вы нажмете **Отмена**, искомый файл будет добавлен к этому списку, и отладчик прекратит поиск этого файла.

## <a name="see-also"></a>См. также

- [Безопасность отладчика](../debugger/debugger-security.md)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)