---
title: Методы отладки CRT | Документация Майкрософт
description: Отладку программы, в которой используется библиотека времени выполнения языка C (CRT), можно выполнять с применением различных методов. В этой статье представлены ссылки на ресурсы, в которых они рассматриваются более подробно.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d5f85584403cc18cd00708a8d4698723d614ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857614"
---
# <a name="crt-debugging-techniques"></a>Методы отладки CRT
Эти методы могут пригодиться при отладке программы с использованием библиотеки времени выполнения языка С (CRT).

## <a name="in-this-section"></a>В этом разделе
 [Работа с библиотекой отладки CRT](../debugger/crt-debug-library-use.md)

 Поддержка отладки для библиотеки CRT и инструкции по применению ее средств.

 [Макросы для создания отчетов](../debugger/macros-for-reporting.md)

 Сведения о макросах **_RPTn** и **_RPTFn** (определенных в CRTDBG.H), заменяющих оператор `printf` для отладки.

 [Версии отладки функций выделения кучи](../debugger/debug-versions-of-heap-allocation-functions.md)

 Специальные отладочные версии функций выделения кучи, содержащие сведения о том, как CRT отображает вызовы, как избежать преобразования, а также преимущества явных вызовов, отслеживание отдельных типов выделений в клиентских блоках и результаты отсутствия описания _DEBUG.

 [Сведения о куче отладки CRT](../debugger/crt-debug-heap-details.md)

 Ссылки на управление памятью и отладочную кучу, типы блоков в отладочной куче, использование кучи, функции отчета о состоянии кучи, отслеживание запросов на выделение кучи.

 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)

 Ссылки на функции-ловушки клиентского блока, функции-ловушки выделения, ловушки выделения и выделения памяти CRT, а также отчетные функции-ловушки.

 [Обнаружение утечек памяти с помощью библиотеки CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)

 Рассматриваются способы обнаружения и изоляции утечек памяти с помощью отладчика и библиотеки времени выполнения языка C (CRT).

## <a name="related-sections"></a>Связанные разделы

- [Отладка машинного кода](../debugger/debugging-native-code.md). Описание некоторых наиболее часто возникающих проблем, связанных с отладкой, и методов отладки для приложений C и C++.
- [Безопасность отладчика](../debugger/debugger-security.md). Рекомендации по безопасной отладке.