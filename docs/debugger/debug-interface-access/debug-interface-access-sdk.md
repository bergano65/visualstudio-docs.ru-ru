---
title: SDK для доступа к интерфейсу отладки | Документация Майкрософт
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915f594a984af41da167e0fd3d58beb2f6ddd978
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554913"
---
# <a name="debug-interface-access-sdk"></a>SDK для доступа к интерфейсу отладки

Отладка интерфейса доступа программного обеспечения средств разработки (SDK для доступа к интерфейсу отладки) предоставляет доступ к отладочной информации, хранящейся в PDB-файлах программы, созданные средствами обработки после компиляции Microsoft. Так как формат PDB-файл, создаваемых средствами обработки после компиляции подвергается постоянным редакции, предоставляя формат непрактично. С помощью API доступа к интерфейсу отладки, можно разрабатывать приложения, искать и просматривать сведения об отладке в PDB-файл. Такие приложения например, отчет с данными обратной трассировки стека и анализировать данные о производительности.

## <a name="in-this-section"></a>Содержание раздела

[Начало работы](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

Обзор пакета SDK для доступа к интерфейсу отладки функции и указывает, где установлен пакет SDK доступа к интерфейсу отладки, а также необходимых файлов заголовков и библиотек.

[Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Инструкции о том, как использовать API доступа к интерфейсу отладки для запроса PDB-файл.

[Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Описывает, как символы и теги символов используются в интерфейсе API для доступа к интерфейсу отладки.

[Ссылки](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

Содержит интерфейсы, методы, перечисления и структуры интерфейса API доступа к интерфейсу отладки.

[Пример файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)

В этой статье описывается использование API доступа к интерфейсу отладки, чтобы искать и просматривать сведения об отладке.
