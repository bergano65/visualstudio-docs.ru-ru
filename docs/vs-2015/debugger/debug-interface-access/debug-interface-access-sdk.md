---
title: SDK для доступа к интерфейсу отладки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 394109e1d691819e06159073a6ea00b65d97de0a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810043"
---
# <a name="debug-interface-access-sdk"></a>SDK для доступа к интерфейсу отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладка интерфейса доступа программного обеспечения средств разработки (SDK для доступа к интерфейсу отладки) предоставляет доступ к отладочной информации, хранящейся в PDB-файлах программы, созданные средствами обработки после компиляции Microsoft. Так как формат PDB-файл, создаваемых средствами обработки после компиляции подвергается постоянным редакции, предоставляя формат непрактично. С помощью API доступа к интерфейсу отладки, можно разрабатывать приложения, искать и просматривать сведения об отладке в PDB-файл. Такие приложения например, отчет с данными обратной трассировки стека и анализировать данные о производительности.  
  
## <a name="in-this-section"></a>В этом разделе  
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
  
 [Файл исходного кода Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Исходный код, используемый [пример файла Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) для демонстрации API доступа к интерфейсу отладки.



