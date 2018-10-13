---
title: Методы отладки CRT | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime.debugging
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34d9f1036349798b56306c41eddbc4f71cfffac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238749"
---
# <a name="crt-debugging-techniques"></a>Методы отладки CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти методы могут пригодиться при отладке программы с использованием библиотеки времени выполнения языка С (CRT).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Работа с библиотекой отладки CRT](../debugger/crt-debug-library-use.md)  
 Поддержка отладки для библиотеки CRT и инструкции по применению ее средств.  
  
 [Макросы для создания отчетов](../debugger/macros-for-reporting.md)  
 Предоставляет сведения о **_RPTn** и **_RPTFn** макросы (определенная в CRTDBG. H), который заменяет собой `printf` для отладки.  
  
 [Версии отладки функций выделения кучи](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Специальные отладочные версии функций выделения кучи, содержащие сведения о том, как CRT отображает вызовы, как избежать преобразования, а также преимущества явных вызовов, отслеживание отдельных типов выделений в клиентских блоках и результаты отсутствия описания _DEBUG.  
  
 [Сведения о куче отладки CRT](../debugger/crt-debug-heap-details.md)  
 Ссылки на управление памятью и отладочную кучу, типы блоков в отладочной куче, использование кучи, функции отчета о состоянии кучи, отслеживание запросов на выделение кучи.  
  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)  
 Ссылки на функции-ловушки клиентского блока, функции-ловушки выделения, ловушки выделения и выделения памяти CRT, а также отчетные функции-ловушки.  
  
 [Обнаружение утечек памяти с помощью библиотеки CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Рассматриваются способы обнаружения и изоляции утечек памяти с помощью отладчика и библиотеки времени выполнения языка C (CRT).  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладка машинного кода](../debugger/debugging-native-code.md)  
 Описание некоторых наиболее часто возникающих проблем, связанных с отладкой, и методов отладки для приложений C и C++.  
  
 [Безопасность отладчика](../debugger/debugger-security.md)  
 Рекомендации по безопасной отладке.



