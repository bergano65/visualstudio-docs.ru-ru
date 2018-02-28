---
title: "Интерфейсы (SDK для доступа к интерфейсу отладки) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e128aa0a4cbb30106981b152252ff308e21669b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="interfaces-debug-interface-access-sdk"></a>Интерфейсы (SDK для доступа к интерфейсу отладки)
Методы перечислены в алфавитном порядке в списке каждого интерфейса в таблице содержимого и на странице интерфейса в порядке таблицы Vtable.  
  
## <a name="in-this-section"></a>В этом разделе  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Предоставляет управление как пакет SDK для рассчитывает виртуального и относительные виртуальные адреса для отладки объектов.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Инициирует доступ к источнику из символов отладки.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Предоставляет доступ для записи в поток данных отладки.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Перечисляет различные потоки отладки, содержащихся в источнике данных.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Перечисляет различные элементы данных кадров, содержащихся в источнике данных.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Перечисление различных источников подставляемого, содержащихся в источнике данных.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Перечисляет различные номера строк, содержащихся в источнике данных.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Перечисляет различные раздел материалов, содержащиеся в источнике данных.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Перечисляет различные сегменты, содержащихся в источнике данных.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Перечисляет различные исходные файлы, содержащиеся в источнике данных.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Перечисляет различные доступные кадры стека.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Перечисляет различные символов, содержащихся в источнике данных.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Перечисляет по адресу различных символов, содержащихся в источнике данных.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Перечисление различных таблицах, содержащихся в источнике данных.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Предоставляет сведения о кадре стека.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Предоставляет сведения о базовых расположение и памяти смещения модуля или образа.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Обращается к исходного кода программы хранятся в источнике данных для доступа к интерфейсу отладки.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Доступ к информации, описание процесса сопоставления из блока байтов текста изображения на номер строки исходного файла.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Получает обратные вызовы от символа DIA поиск процедур, что позволяет пользовательский интерфейс для отчетов о ходе попытки расположение.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Получает обратные вызовы от символа DIA поиск процедур, что ограничения, налагаемые на процесс поиску.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Позволяет читать постоянными свойствами DIA набора свойств.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Позволяет клиентскому приложению для предоставления байт исполняемого файла в соответствии с позиции в файле.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Позволяет клиентскому приложению для предоставления байт исполняемого файла в соответствии с относительный виртуальный адрес.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Извлекает данные, описывающие вклад раздела, то есть непрерывный блок памяти, представленные в образе компилируемого объекта.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Сопоставляет данные из номер раздела в сегменты адресного пространства.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Предоставляет контекст запроса для отладочных символов.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Представляет исходный файл.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Предоставляет свойства кадра стека.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Предоставляет методы, чтобы сделать стек стека с помощью PDB-файл.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Поддерживает стек контекста между вызовами [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) метод.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Облегчает прохода по стеку, с помощью файла базы данных (PDB) для отладки программы.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Описывает свойства экземпляра символа.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Перечисляет таблицы источника данных доступа к интерфейсу отладки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Описывает, перечисления и структуры, используемые в различных интерфейсов DIA SDK.  
  
 [Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Описывает константы, доступные в пакете SDK для доступа к интерфейсу отладки.  
  
## <a name="see-also"></a>См. также  
 [Ссылки](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)