---
title: Использование библиотеки отладки CRT | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51534d226f3ae0f8726bb818423bf0a9b788fd8c
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "58980069"
---
# <a name="crt-debug-library-use"></a>Работа с библиотекой отладки CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Библиотека CRT предоставляет расширенную отладочную поддержку. Чтобы использовать отладочные библиотеки CRT, необходимо связать с [/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) и скомпилируйте его с **/MDd**, **/MTd**, или **/LDd**.  
  
## <a name="remarks"></a>Примечания  
 Основные определения и макросы для отладки CRT содержатся в файле заголовка CRTDBG.h.  
  
 Функции в отладочных библиотеках CRT компилируются с отладочными сведениями ([/Z7, /Zd, /Zi, /ZI (формат отладочной информации)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) и без оптимизации. Некоторые функции содержат утверждения для проверки передаваемых им параметров, для них приведен исходный код. Исходный код позволяет войти в функцию CRT, чтобы убедиться, что она работает в соответствии с ожиданиями, а также проверить функцию на наличие некорректных параметров или состояний памяти. (Некоторые технологии CRT запатентованы, поэтому для них не предоставляется исходный код для обработки исключений, плавающей запятой и некоторых других программ.)  
  
 В процессе установки Visual C++ можно выбрать параметр, позволяющий разрешить или запретить копирование исходного кода CRT на жесткий диск. Если не устанавливать исходный код, то для захода в некоторые функции CRT понадобится CD-ROM.  
  
 Дополнительные сведения о различных библиотеках времени выполнения см. в разделе [Библиотеки времени выполнения C](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (использование библиотеки времени выполнения)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
