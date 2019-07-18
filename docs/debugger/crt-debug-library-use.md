---
title: Использование библиотеки отладки CRT | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 9434be46f357a97ad01f10ceec184ebe6c52eb43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565551"
---
# <a name="crt-debug-library-use"></a>Работа с библиотекой отладки CRT
Библиотека CRT предоставляет расширенную отладочную поддержку. Чтобы использовать отладочные библиотеки CRT, необходимо связать с [/DEBUG](/cpp/build/reference/debug-generate-debug-info) и скомпилируйте его с **/MDd**, **/MTd**, или **/LDd**.

## <a name="remarks"></a>Примечания
 Основные определения и макросы для отладки CRT содержатся в файле заголовка CRTDBG.h.

 Функции в отладочных библиотеках CRT компилируются с отладочными сведениями ([/Z7, /Zd, /Zi, /ZI (формат отладочной информации)](/cpp/build/reference/z7-zi-zi-debug-information-format)) и без оптимизации. Некоторые функции содержат утверждения для проверки передаваемых им параметров, для них приведен исходный код. Исходный код позволяет войти в функцию CRT, чтобы убедиться, что она работает в соответствии с ожиданиями, а также проверить функцию на наличие некорректных параметров или состояний памяти. (Некоторые технологии CRT запатентованы, поэтому для них не предоставляется исходный код для обработки исключений, плавающей запятой и некоторых других программ.)

 В процессе установки Visual C++ можно выбрать параметр, позволяющий разрешить или запретить копирование исходного кода CRT на жесткий диск. Если не устанавливать исходный код, то для захода в некоторые функции CRT понадобится CD-ROM.

 Дополнительные сведения о различных библиотеках времени выполнения см. в разделе [Библиотеки времени выполнения C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>См. также

- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (использование библиотеки времени выполнения)](/cpp/build/reference/md-mt-ld-use-run-time-library)