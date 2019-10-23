---
title: Использование библиотеки отладки CRT | Документация Майкрософт
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20aeee220bec600c2232286d18600b04201ad03b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745611"
---
# <a name="crt-debug-library-use"></a>Работа с библиотекой отладки CRT
Библиотека CRT предоставляет расширенную отладочную поддержку. Чтобы использовать одну из библиотек отладки CRT, необходимо выполнить компоновку с параметром [/Debug](/cpp/build/reference/debug-generate-debug-info) и компилировать с параметром **/MDD**, **/MTD**или **/LDD**.

## <a name="remarks"></a>Заметки
 Основные определения и макросы для отладки CRT содержатся в файле заголовка CRTDBG.h.

 Функции в отладочных библиотеках CRT компилируются с отладочными сведениями ([/Z7, /Zd, /Zi, /ZI (формат отладочной информации)](/cpp/build/reference/z7-zi-zi-debug-information-format)) и без оптимизации. Некоторые функции содержат утверждения для проверки передаваемых им параметров, для них приведен исходный код. Исходный код позволяет войти в функцию CRT, чтобы убедиться, что она работает в соответствии с ожиданиями, а также проверить функцию на наличие некорректных параметров или состояний памяти. (Некоторые технологии CRT запатентованы, поэтому для них не предоставляется исходный код для обработки исключений, плавающей запятой и некоторых других программ.)

 Дополнительные сведения о различных библиотеках времени выполнения см. в разделе [Библиотеки времени выполнения C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>См. также

- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (использование библиотеки времени выполнения)](/cpp/build/reference/md-mt-ld-use-run-time-library)