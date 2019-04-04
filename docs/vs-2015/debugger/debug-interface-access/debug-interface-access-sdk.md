---
title: SDK для доступа к интерфейсу отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991415"
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
