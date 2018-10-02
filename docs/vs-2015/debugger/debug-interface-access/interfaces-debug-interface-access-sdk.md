---
title: Интерфейсы (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 430d310b4a42440d827dcefd209579b36eda9807
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573356"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Интерфейсы (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [интерфейсы (Отладка интерфейса Access SDK)](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/interfaces-debug-interface-access-sdk).  
  
Методы в алфавитном порядке отображаются в категории каждого интерфейса в таблице, содержимого и на странице интерфейс в порядке таблицы Vtable.  
  
## <a name="in-this-section"></a>В этом разделе  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Позволяет контролировать как пакет SDK для доступа к интерфейсу отладки рассчитывает виртуального и относительного виртуального адреса для отладки объектов.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Инициирует доступ к источнику отладочные символы.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Предоставляет доступ к записям в поток данных отладки.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Перечисляет различные потоки отладки, содержащихся в источнике данных.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Перечисляет различные элементы данных кадров, содержащихся в источнике данных.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Перечисление различных внедренного источников, содержащихся в источнике данных.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Перечисляет различные номера строк, содержащихся в источнике данных.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Перечисляет различные разделе материалов, содержащихся в источнике данных.  
  
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
 Перечисляет различных таблицах, содержащихся в источнике данных.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Предоставляет сведения о кадре стека.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Предоставляет сведения о базового смещения расположения и памяти модуля или изображения.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Обращений к исходного кода программы, которые хранятся в источнике данных для доступа к интерфейсу отладки.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Доступ к информации, описание процесса сопоставления из блок байтов изображение текста на номер строки исходного файла.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Получает обратные вызовы из символа доступа к интерфейсу отладки, поиск процедуры, что позволяет пользовательский интерфейс для отчета о ходе попытки расположение.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Получает обратные вызовы из символа доступа к интерфейсу отладки, поиск процедуры, что позволяет ограничения, которые необходимо соблюдать на процесс поиску.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Позволяет считывать свойства постоянный набор свойств для доступа к интерфейсу отладки.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Позволяет клиентскому приложению для предоставления байт исполняемого файла, как указано по позиции файла.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Позволяет клиентскому приложению для предоставления байт исполняемого файла, как указано по относительному виртуальному адресу.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Извлекает данные, описывающие вклад раздела, то есть непрерывный блок памяти порожденного к образу единице компиляции.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Сопоставляет данные из номер раздела в сегменты адресного пространства.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Предоставляет контекст запроса для символов отладки.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Представляет исходный файл.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Предоставляет свойства кадра стека.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Предоставляет методы, чтобы сделать стек стека с помощью PDB-файл.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Поддерживает контекст стека между вызовами [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) метод.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Упрощает анализ стека с помощью файла базы данных (PDB) программы отладки.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Описывает свойства экземпляра символа.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Перечисляет таблицы источника данных доступа к интерфейсу отладки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Описывает перечисления и структуры, используемые различными интерфейсами пакета SDK для доступа к интерфейсу отладки.  
  
 [Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Описывает константы, доступные в пакете SDK для доступа к интерфейсу отладки.  
  
## <a name="see-also"></a>См. также  
 [Ссылки](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)



