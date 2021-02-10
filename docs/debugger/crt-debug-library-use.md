---
title: Работа с библиотекой отладки CRT | Документация Майкрософт
description: Сведения о поддержке отладки в библиотеке CRT, а также о том, как использовать отладочные библиотеки CRT.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe50082f8ff62c4a19b7725facc18f43d672e353
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865713"
---
# <a name="crt-debug-library-use"></a>Работа с библиотекой отладки CRT
Библиотека CRT предоставляет расширенную отладочную поддержку. Чтобы использовать отладочные библиотеки CRT, необходимо скомпоновать их с помощью [/DEBUG](/cpp/build/reference/debug-generate-debug-info), а затем скомпилировать с параметром **/MDd**, **/MTd** или **/LDd**.

## <a name="remarks"></a>Примечания
 Основные определения и макросы для отладки CRT содержатся в файле заголовка CRTDBG.h.

 Функции в отладочных библиотеках CRT компилируются с отладочными сведениями ([/Z7, /Zd, /Zi, /ZI (формат отладочной информации)](/cpp/build/reference/z7-zi-zi-debug-information-format)) и без оптимизации. Некоторые функции содержат утверждения для проверки передаваемых им параметров, для них приведен исходный код. Исходный код позволяет войти в функцию CRT, чтобы убедиться, что она работает в соответствии с ожиданиями, а также проверить функцию на наличие некорректных параметров или состояний памяти. (Некоторые технологии CRT запатентованы, поэтому для них не предоставляется исходный код для обработки исключений, плавающей запятой и некоторых других программ.)

 Дополнительные сведения о различных библиотеках времени выполнения см. в разделе [Библиотеки времени выполнения C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>См. также

- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (использование библиотеки времени выполнения)](/cpp/build/reference/md-mt-ld-use-run-time-library)