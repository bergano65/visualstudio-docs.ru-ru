---
title: Интерфейсы (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0aa48ae0d3c3b6b05ea469baea1a1e1aa106667
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738700"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Интерфейсы (SDK для доступа к интерфейсу отладки)
Методы перечислены в алфавитном порядке под каждым интерфейсом в содержании и на странице интерфейса в порядке vtable.

## <a name="in-this-section"></a>Содержание

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

Предоставляет контроль над тем, как пакет SDK DIA рассчитывает виртуальные и относительные виртуальные адреса для объектов отладки.

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

Инициирует доступ к источнику отладочных символов.

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

Предоставляет доступ к записям в потоке данных отладки.

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

Перечисляет различные потоки отладки, содержащиеся в источнике данных.

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

Перечисляет различные элементы данных кадра, содержащиеся в источнике данных.

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

Перечисление различных внедренных источников, содержащихся в источнике данных.

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

Перечисляет различные номера строк, содержащиеся в источнике данных.

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

Перечисляет различные вклады разделов, содержащиеся в источнике данных.

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

Перечисляет различные сегменты, содержащиеся в источнике данных.

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

Перечисляет различные исходные файлы, содержащиеся в источнике данных.

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

Перечисляет различные доступные кадры стека.

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

Перечисляет различные символы, содержащиеся в источнике данных.

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

Перечисляет по адресу различные символы, содержащиеся в источнике данных.

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

Перечисляет различные таблицы, содержащиеся в источнике данных.

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

Предоставляет сведения о кадре стека.

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

Предоставляет подробные сведения о базовом расположении и смещениях памяти для модуля или изображения.

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

Обращается к исходному коду программы, хранящемуся в источнике данных DIA.

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

Обращается к сведениям, описывающим процесс сопоставления из блока байтов текста изображения с номером строки исходного файла.

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

Получает обратные вызовы из процедуры поиска символов DIA, тем самым позволяя пользовательскому интерфейсу сообщать о ходе попытки расположения.

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

Получает обратные вызовы из процедуры поиска символов DIA, позволяя налагать ограничения на процесс обнаружения.

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

Позволяет считывать постоянные свойства набора свойств DIA.

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

Позволяет клиентскому приложению предоставлять байты исполняемого файла, как указано положением файла.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

Позволяет клиентскому приложению предоставлять байты исполняемого файла, как указано в относительном виртуальном адресе.

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

Извлекает данные, описывающие вклад раздела, то есть непрерывный блок памяти, внесенный в изображение с помощью компилируемого объекта.

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

Сопоставляет данные из номера раздела с сегментами адресного пространства.

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

Предоставляет контекст запроса для отладочных символов.

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

Представляет исходный файл.

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

Предоставляет свойства кадра стека.

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

Предоставляет методы для прохода по стеку с помощью PDB-файла.

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

Поддерживает контекст стека между вызовами метода [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

Облегчает проход по стеку с помощью файла базы данных отладки (PDB) программы.

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

Описывает свойства экземпляра символа.

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

Перечисляет таблицу источника данных DIA.

## <a name="related-sections"></a>Связанные разделы
[Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)

Описывает перечисления и структуры, используемые различными интерфейсами пакета SDK DIA.

[Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

Описывает константы, доступные в пакете SDK для DIA.

## <a name="see-also"></a>См. также

- [Ссылка](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)